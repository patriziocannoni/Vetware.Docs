# VETWARE — Telas de Cadastro

> **Status:** Rascunho v1
> **Origem:** Quebra da seção "2. Cadastro e Perfis" de `Especificacao/Vetware.md` e do item "Cadastro de clínicas/pet shops/clientes/pets" (bloco 🟢 NOW) de `Especificacao/Negocio/Vetware-Product-First.md`, em telas candidatas.
> **Como ler este documento:** cada tela abaixo é uma hipótese de divisão de UI para a funcionalidade de cadastro. Ainda não valida fluxo de navegação, apenas enumera as telas necessárias.

---

## Telas de Cadastro

### Cadastro de Prestadores (lado da oferta)

1. **Cadastro de Clínica/Hospital Veterinário**
   Dados do negócio:
   - Nome Fantasia
   - Razão Social
   - CNPJ
   - Telefone
   - Endereço
   - Especialidades
   - Horário de funcionamento
   - Descrição do negócio
   - Imagem do negócio
   - Email
   - Site
   - Horário de funcionamento
   - Imagem do negócio

2. **Cadastro de Pet Shop**
   Dados do negócio:
   - Nome Fantasia
   - Razão Social
   - CNPJ
   - Telefone
   - Endereço
   - Serviços oferecidos
   - Horário de funcionamento
   - Descrição do negócio
   - Imagem do negócio
   - Email
   - Site
   - Horário de funcionamento
   - Imagem do negócio

3. **Cadastro de Equipe/Colaboradores**
   Vincular veterinários e atendentes a uma clínica/pet shop, com definição de papel/permissão (admin, veterinário, atendente).

### Cadastro de Clientes (lado da demanda)

4. **Cadastro de Tutor (Cliente)**
   Dados pessoais, contato, endereço.

5. **Cadastro de Pet**
   Vinculado a um tutor (espécie, raça, idade, peso, particularidades clínicas).

### Cadastro/Perfil transversal

6. **Perfil de Usuário/Conta**
   Dados de login, credenciais, papéis e permissões (ligado à seção "1. Autenticação e Autorização"; costuma aparecer como tela de "meu perfil"/"editar perfil").

7. **Onboarding/Seleção de Perfil**
   Tela inicial pós-cadastro para definir se o usuário é tutor, admin de clínica, veterinário, etc. (necessária quando o mesmo cadastro de conta pode assumir papéis diferentes).

---

## Resumo

- **5 telas núcleo:** Clínica, Pet Shop, Equipe, Tutor, Pet.
- **2 telas de suporte:** Conta/Perfil e Onboarding.

Todas dentro do bloco 🟢 NOW do roadmap ("Cadastro de clínicas/pet shops/clientes/pets" — `Vetware-Product-First.md`, seção 6).

---

## Próximos Passos Sugeridos

1. Validar fluxo de navegação entre as telas (ex: onboarding → escolha de perfil → cadastro específico).
2. Definir wireframes/mockups para cada tela.
3. Confirmar campos obrigatórios x opcionais em cada cadastro com stakeholders.
4. Revisar este documento após validação com design/UX.
