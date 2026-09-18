# VETWARE — Cadastro de Prestadores (lado da oferta)

> **Status:** Proposta de refinamento para validação.
> 
> **Base:** revisão de `Vetware.md` e `Telas-Cadastro.md`.

---

## Objetivo

Permitir que uma clínica, hospital veterinário ou pet shop crie e publique seu perfil no marketplace, informe sua oferta de serviços e convide sua equipe.

## Pontos identificados no rascunho original

- Clínica/hospital e pet shop repetem quase toda a estrutura de cadastro.
- "Serviços oferecidos" e "especialidades" precisam ser dados estruturados, não apenas texto livre.
- Não há fluxo de validação, publicação do perfil nem estados do cadastro.
- O vínculo da equipe não define convite, aceite, permissões ou dados profissionais do veterinário.
- Faltam regras para CNPJ único, endereço, unidade, responsável, atendimento emergencial e alteração de dados validados.

## Direção proposta

Substituir os cadastros separados de clínica/hospital e pet shop por um fluxo único: **Cadastro de Estabelecimento Prestador**.

O tipo do estabelecimento e seus serviços determinam quais campos condicionais serão exibidos. Dessa forma, uma clínica que também oferece banho e tosa não precisa manter dois cadastros.

## Escopo inicial

### Tipos de estabelecimento

- Clínica veterinária
- Hospital veterinário
- Pet shop
- Múltiplos tipos, quando o mesmo estabelecimento oferece serviços combinados

### Fora do escopo inicial

- Cadastro de prestador autônomo sem estabelecimento.
- Catálogo detalhado de produtos, preços, estoque e delivery.
- Agenda por profissional e prontuário clínico.

---

## Fluxo de cadastro

1. Criação ou acesso à conta do responsável.
2. Escolha do tipo de estabelecimento e dos serviços principais.
3. Preenchimento dos dados legais e do responsável.
4. Definição de endereço e disponibilidade operacional.
5. Montagem do perfil público e inclusão de imagens.
6. Envio para validação.
7. Após aprovação, convite e gestão da equipe.

O perfil só deve aparecer nos resultados de busca quando estiver validado e publicado.

---

## Dados do estabelecimento

### Identificação e dados legais

- **Nome fantasia** — obrigatório; público.
- **Razão social** — obrigatório; privado.
- **CNPJ** — obrigatório, único na plataforma e validado.
- **E-mail comercial** — obrigatório.
- **Telefone comercial** — obrigatório.
- **Nome e contato do responsável pelo cadastro** — obrigatórios.
- **Site e redes sociais** — opcionais.

### Localização e atendimento

- **CEP, logradouro, número, complemento, bairro, cidade e UF** — obrigatórios.
- **Referência e coordenadas geográficas** — geradas a partir do endereço.
- **Modalidades de atendimento** — no estabelecimento, domiciliar e/ou remoto; este último conforme evolução do produto.
- **Indicador de atendimento emergencial**.
- **Indicador de operação 24 horas**.

### Oferta

- **Tipo(s) de estabelecimento** — obrigatório.
- **Categorias de serviços** — obrigatório; seleção estruturada.
- **Especialidades veterinárias** — obrigatórias apenas para clínica/hospital, quando aplicável.
- **Descrição institucional** — obrigatória, com limite de caracteres.
- **Serviços e preços detalhados** — evolução futura; no MVP, o estabelecimento informa apenas categorias para descoberta.

### Perfil público

- **Logo ou foto principal** — recomendada.
- **Galeria de imagens** — opcional.
- **Horários por dia da semana**, incluindo abertura, fechamento e intervalos.
- **Exceções de horário**, como feriados — evolução futura.

---

## Validação e publicação

### Estados do cadastro

- **Rascunho:** cadastro ainda não enviado.
- **Em validação:** dados submetidos à análise.
- **Pendente de ajustes:** há informações ou documentos a corrigir.
- **Aprovado não publicado:** validado, mas invisível na busca.
- **Publicado:** visível ao público.
- **Suspenso:** indisponível temporariamente.

Alterações de CNPJ, razão social, endereço ou tipo de estabelecimento podem exigir nova validação. Nome fantasia, descrição, fotos e horários podem seguir regras mais simples.

---

## Equipe e permissões

O cadastro de equipe ocorre dentro do estabelecimento, e não como um cadastro isolado.

- O administrador convida uma pessoa por e-mail.
- A pessoa aceita o convite e completa seus próprios dados.
- Nenhuma senha é criada ou compartilhada pelo administrador.
- Um usuário pode participar de mais de um estabelecimento.

### Papéis iniciais

- **Proprietário:** controle total, inclusive titularidade e publicação.
- **Administrador:** gerencia perfil, horários, equipe e operação.
- **Veterinário:** completa dados profissionais, como CRMV e UF; futuramente acessará funções clínicas.
- **Atendente:** opera agenda e atendimento, com permissões restritas.

---

## Regras de aceite

- Um CNPJ só pode ter um cadastro ativo por estabelecimento/unidade. Se já existir, o usuário deve solicitar acesso.
- O estabelecimento deve manter ao menos um proprietário ativo.
- CRMV e UF são obrigatórios para usuários com papel de veterinário.
- Dados legais não devem ser exibidos integralmente no perfil público.
- O cadastro não deve armazenar dados clínicos de pets nesta etapa.

---

## Decisão em aberto

No MVP, cada CNPJ representará uma única unidade física ou será necessário suportar redes com várias unidades desde o início?

**Recomendação:** cadastrar uma unidade por perfil no MVP, mas estruturar o domínio para que uma organização possa possuir várias unidades posteriormente.
