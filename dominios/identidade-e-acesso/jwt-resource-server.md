# JWT Resource Server

## Contrato

- Vetware.Auth emite JWT HS256; Vetware.Backend é somente resource server.
- A chave compartilhada é `spring.jwt.key`.
- Validar assinatura, issuer `Vetware.Auth`, `exp` e `iat`.
- `sub` e lista `scope` existem, sem validação adicional atual; não há `aud`.

## Backend

Usar `spring-boot-starter-oauth2-resource-server`, `NimbusJwtDecoder` com secret HMAC e `MacAlgorithm.HS256`, além de `JwtValidators.createDefaultWithIssuer("Vetware.Auth")`. A API é stateless, sem CSRF, e toda rota de negócio exige autenticação; health, Swagger e api-docs podem ser bypass explícito.

## CORS e resultado

Origens ficam no YAML do profile ativo. Permitir `Authorization`, OPTIONS e os métodos usados. Token ausente, inválido, expirado ou com issuer diferente retorna 401; token válido segue ao controller.
