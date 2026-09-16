# BACKEND JWT RESOURCE SERVER - ESPECIFICAÇÃO

## Contexto
- Vetware.Auth já emite JWT (HS256, segredo simétrico `spring.jwt.key`, issuer `Vetware.Auth`).
- Vetware.Backend hoje não valida esse token. Os endpoints REST devem exigir Bearer JWT emitido pelo Auth.
- Clientes previstos: Vetware.Frontend (chamada REST) e clientes manuais (Postman, Bruno).
- Esta spec cobre só o Backend como resource server. Emissão de token continua exclusiva do Auth.

## Fora de escopo
- Login, `/auth/token`, PasswordEncoder e persistência de credenciais no Backend.
- JwtEncoder no Backend.
- JWKS, chave assimétrica (RSA/EC) e discovery OIDC (`issuer-uri`).
- Autorização fina por perfil de negócio (clínica, veterinário, cliente). O Auth ainda manda roles fixas.
- Implementar interceptor HTTP no Frontend (necessário depois; não bloqueia o Backend).

## Papel de cada módulo
- Vetware.Auth: authorization server customizado. POST `/vetware-auth/auth/token` (client_credentials). Assina HS256.
- Vetware.Backend: resource server. Não emite token. Valida assinatura, issuer e expiração.
- Vetware.Frontend: obtém `acessToken` do Auth, guarda em sessionStorage e deve enviar `Authorization: Bearer <token>` nas chamadas ao Backend (trabalho futuro no Frontend).

## Contrato do token (fonte: AuthService)
- Algoritmo: HS256 (HMAC-SHA256).
- Chave: string simétrica compartilhada (`spring.jwt.key`). Mesmo valor no Auth e no Backend.
- Header: `Authorization: Bearer <jwt>`.
- Claims obrigatórias a validar:
  - `iss` = `Vetware.Auth` (string literal, não é URL).
  - `exp` e `iat` (validade atual: 1 hora).
  - assinatura HMAC com a chave compartilhada.
- Claims presentes, sem validação extra nesta entrega:
  - `sub` = e-mail / client_id.
  - `scope` = lista JSON `["ROLE_ADMIN", "ROLE_USER"]` (hoje hardcoded no Auth).
- `aud` não é emitido. Não validar audience.

## Dependências Maven (Vetware.Backend)
- Manter: `spring-boot-starter-security`.
- Adicionar: `spring-boot-starter-oauth2-resource-server`.
- Remover: `spring-boot-starter-oauth2-authorization-server` (emissão de token não é papel do Backend).
- O starter de resource server traz Nimbus/`JwtDecoder` compatível com o encoder do Auth.

## Configuração Java (pacote `br.com.vetware.backend.config`)
- `JwtConfig`: bean `JwtDecoder` com `NimbusJwtDecoder.withSecretKey(...)` e `MacAlgorithm.HS256`.
  - SecretKey a partir de `spring.jwt.key` (bytes UTF-8, algoritmo HmacSHA256).
  - Validator: `JwtValidators.createDefaultWithIssuer("Vetware.Auth")`.
- `RequestSecurityConfig` (ou nome equivalente já usado no Auth):
  - CSRF desabilitado (API REST).
  - Sessão STATELESS.
  - `oauth2ResourceServer().jwt(...)` usando o bean `JwtDecoder`.
  - `anyRequest().authenticated()` para endpoints de negócio.
  - `permitAll` apenas para bypass explícito (health, swagger, api-docs), no mesmo espírito do Auth.
- Não usar `spring.security.oauth2.resourceserver.jwt.issuer-uri`. Isso dispara JWKS/OIDC e não existe no Auth.
- Authorities: o conversor padrão do Spring costuma esperar `scope`/`scp` como string separada por espaço. O Auth envia lista. Se `hasRole`/`hasAuthority` falhar, usar `JwtAuthenticationConverter` que leia a lista `scope`. `.authenticated()` não depende disso.

## YAML
- Propriedade `spring.jwt.key` nos profiles local/dev/prod, com o mesmo valor do Auth daquele ambiente.
- Origem(s) CORS do Frontend no YAML do profile (`application-local.yml` agora; `application-dev.yml` / `application-prd.yml` no futuro), não no `application.yml` compartilhado.
- Lista opcional `spring.security.custom.by-pass` para paths públicos.
- Não reutilizar o `issuer-uri` de Keycloak que existe hoje no YAML de teste.
- Segredo de produção via variável de ambiente / secret manager, não commitado.

## CORS
- Origem do Frontend não fica hardcoded no Java. Cada ambiente declara a origem (ou origens) no YAML do profile Spring Boot.
- Hoje existe só `application-local.yml` (ex.: `http://localhost:4200`). No futuro haverá profiles adicionais no mesmo padrão, por exemplo `application-dev.yml` e `application-prd.yml`, cada um com a origem daquele ambiente.
- A `CorsConfigurationSource` lê essa propriedade do YAML ativo (`spring.profiles.active`).
- Permitir header `Authorization` e métodos GET, POST, PUT, OPTIONS (e os demais usados pelos controllers).
- Preferir `CorsConfigurationSource` global na `SecurityFilterChain`, não só `@CrossOrigin` pontual (hoje Loja não tem CORS).
- Sem CORS correto, Bruno/Postman passam e o browser falha no preflight.

## Endpoints protegidos (base `http://localhost:8090/vetware-backend`)
- GET `/enderecos/{cep}`
- PUT `/enderecos`
- GET `/usuarios/{id}`
- POST `/usuarios`
- GET `/lojas/{id}`
- GET `/lojas`
- POST `/lojas`
- Demais endpoints de negócio futuros, salvo bypass explícito.

## Comportamento esperado
- Sem header Authorization, token ausente, malformado, assinatura inválida, issuer diferente ou expirado: HTTP 401.
- Token válido: request segue para o controller.
- OPTIONS de CORS (preflight): não deve exigir JWT se configurado corretamente.

## Como testar (Bruno / Postman)
1. POST `http://localhost:9090/vetware-auth/auth/token` com `client_id`, `client_secret`, `grant_type=client_credentials` (`application/x-www-form-urlencoded`).
2. Copiar o campo `acessToken` (grafia atual do DTO do Auth).
3. GET/POST no Backend com header `Authorization: Bearer <acessToken>`.
4. Repetir sem header e com token adulterado: esperar 401.

## Frontend (dependência posterior, fora desta entrega do Backend)
- Interceptor HTTP que leia `sessionStorage.token` e anexe `Authorization: Bearer`.
- Sem isso, após o Backend ficar protegido, o Angular receberá 401 mesmo com login ok.

## Riscos e decisões conscientes
- Chave simétrica compartilhada: rotação invalida todos os tokens de imediato; Auth e Backend precisam atualizar juntos.
- Não há JWKS; distribuição da chave é operacional (YAML/env).
- Roles no token ainda não refletem perfis reais do produto (admin, veterinário, atendente, cliente).
- Campo `acessToken` no Auth tem typo; clientes devem usar o nome atual até haver breaking change.

## Critérios de aceite
- Chamada autenticada com JWT válido do Auth retorna o status de negócio (2xx/4xx de aplicação), não 401 de segurança.
- Chamada sem Bearer ou com JWT inválido/expirado retorna 401.
- Swagger/actuator definidos como bypass continuam acessíveis sem token.
- CORS usa a origem do Frontend definida no YAML do profile ativo e permite enviar Authorization.
- Backend não emite token e não depende de Keycloak/JWKS.
