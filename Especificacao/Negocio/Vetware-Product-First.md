# VETWARE — Especificação Product-First

> **Status:** Rascunho v1 (hipóteses a validar com stakeholders/mercado)
> **Origem:** Reestruturação do escopo funcional em `Specs/Vetware.md` sob a lente Product-First (Problema → Persona/JTBD → Valor → Outcomes → Modelo de Negócio → Features).
> **Como ler este documento:** cada feature do escopo original só existe aqui se estiver amarrada a uma persona, a um "job" e a um outcome. Onde não há evidência coletada ainda, isso está marcado explicitamente como **[HIPÓTESE]**.

---

## 1. Contexto e Problema

O mercado pet (clínicas, hospitais veterinários, pet shops e tutores) hoje opera de forma fragmentada:

| Sintoma | Impacto |
|---|---|
| Descoberta de serviços veterinários é manual (indicação, Google, grupos de WhatsApp) | Tutor perde tempo e confiança; clínicas boas mas pouco conhecidas não crescem |
| Agendamento por telefone/WhatsApp, sem confirmação estruturada | Fila, no-show, atrito operacional para a clínica |
| Histórico do pet fica espalhado entre clínicas, carteirinhas de papel e memória do tutor | Perda de informação clínica relevante, risco em emergências, retrabalho de exames |
| Emergências dependem de sorte/rede de contatos do tutor | Risco à vida do animal, ansiedade do tutor |
| Compra de produtos pet (ração, medicamento) desconectada do cuidado clínico | Pet shops e clínicas não capturam a demanda recorrente de forma integrada |
| Falta de reputação estruturada e comparável entre prestadores | Tutor decide "no escuro"; bons prestadores não se diferenciam |
| Clínicas pequenas não têm escala para negociar exames/insumos entre si | Ineficiência de custo, menor competitividade frente a redes grandes |

**Problema central (hipótese de tese de produto):**
> Tutores de pets não conseguem encontrar, confiar e agendar cuidado veterinário de qualidade com a mesma facilidade com que resolvem qualquer outra necessidade cotidiana — e prestadores (clínicas, hospitais, pet shops) não têm uma plataforma única que capture toda a jornada do pet (descoberta → atendimento → histórico → recompra).

---

## 2. Personas e Jobs-to-be-Done (JTBD)

> Personas inferidas a partir do escopo funcional atual. **[HIPÓTESE]** — precisam de validação com entrevistas/dados reais.

### 2.1 Tutor do Pet (Cliente — usuário final B2C)

- **Contexto:** dono de um ou mais pets, varia de "tutor de primeira viagem" a "tutor experiente com pet idoso/crônico".
- **Dores:** ansiedade em emergências, dificuldade de achar prestador confiável, esquecer vacinas/retornos, histórico do pet disperso.
- **Jobs funcionais:** "Quando meu pet precisa de cuidado, quero encontrar rapidamente um prestador qualificado, disponível e no orçamento que eu confio."
- **Jobs emocionais:** "Quero sentir que estou cuidando bem do meu pet e que, numa emergência, não vou ficar perdido."
- **Jobs sociais:** "Quero poder recomendar/ser visto como um bom tutor."
- **Definição de sucesso:** agenda um atendimento em poucos minutos, recebe confirmação, tem o histórico do pet sempre à mão, é alertado antes de esquecer algo importante.

### 2.2 Clínica / Hospital Veterinário (Prestador de serviço — B2B2C, lado da oferta)

- **Contexto:** de clínicas de bairro (1-3 veterinários) a hospitais/redes maiores.
- **Dores:** agenda subotimizada (ociosidade x fila), aquisição de novos clientes cara/imprevisível, dificuldade de diferenciação por reputação, falta de padronização no histórico clínico entre parceiros.
- **Jobs funcionais:** "Quero preencher minha agenda com clientes qualificados e reduzir no-show."
- **Jobs emocionais:** "Quero ser reconhecida pela qualidade do meu atendimento, não só pelo preço."
- **Definição de sucesso:** aumento de ocupação da agenda, redução de no-show, mais avaliações positivas, acesso a parcerias B2B para exames/cirurgias que não consegue oferecer sozinha.

### 2.3 Pet Shop (Prestador de produto/serviço de bem-estar — B2B2C, lado da oferta)

- **Contexto:** desde pet shops de bairro até redes com banho/tosa e e-commerce próprio.
- **Dores:** competição com marketplaces genéricos, dificuldade de fidelizar cliente recorrente (ração, banho), baixa visibilidade digital.
- **Jobs funcionais:** "Quero vender de forma recorrente para tutores que já confiam em mim e capturar demanda de quem está perto."
- **Definição de sucesso:** aumento de recompra (ração/produtos recorrentes), agenda de banho e tosa ocupada, integração com clínicas parceiras para cross-sell.

### 2.4 Veterinário / Atendente (Usuário operacional dentro da clínica/pet shop)

- **Contexto:** profissional que efetivamente atende, registra prontuário, opera a agenda no dia a dia.
- **Dores:** retrabalho de cadastro, falta de contexto do histórico do pet na hora da consulta, telefone/WhatsApp tomando tempo do atendimento.
- **Jobs funcionais:** "Quero ver o histórico completo do pet antes/durante a consulta e gerenciar minha agenda sem fricção."
- **Definição de sucesso:** menos tempo administrativo, decisões clínicas mais informadas, menos erro de comunicação com o tutor.

### 2.5 Administrador da Clínica/Pet Shop (Gestor do negócio na plataforma)

- **Contexto:** responsável por cadastro, equipe, precificação, e (no futuro) monetização/assinatura na Vetware.
- **Jobs funcionais:** "Quero gerenciar meu negócio, minha equipe e meus resultados na plataforma com o mínimo de esforço, e entender meu retorno sobre o que pago pra estar aqui."
- **Definição de sucesso:** visibilidade de métricas de performance (ocupação, avaliações, receita gerada via plataforma), controle de permissões da equipe.

---

## 3. Proposta de Valor

| Segmento | Dor aliviada | Ganho criado | Proposta de valor (1 frase) |
|---|---|---|---|
| Tutor | Não sei em quem confiar / não acho horário / esqueço vacina / perco histórico | Descoberta rápida, confiável, histórico centralizado, alertas proativos | "Encontre, agende e acompanhe o cuidado do seu pet em um só lugar, com quem você pode confiar." |
| Clínica/Hospital | Agenda ociosa, aquisição cara, reputação não capturada | Demanda qualificada, redução de no-show, prova social, parcerias B2B | "Preencha sua agenda com clientes qualificados e construa sua reputação digital." |
| Pet Shop | Baixa recorrência, pouca visibilidade | Cliente recorrente capturado via jornada do pet, cross-sell com clínicas | "Transforme cuidado pontual em recompra recorrente." |
| Veterinário/Atendente | Retrabalho, falta de contexto | Contexto clínico completo, menos fricção operacional | "Atenda com o histórico completo do pet na mão." |
| Admin | Falta de visibilidade de performance/ROI | Métricas de negócio, gestão de equipe | "Gerencie seu negócio veterinário com dados, não achismo." |

**Proposta de valor da plataforma (síntese):**
> Vetware é o marketplace que une, numa única jornada, a descoberta de prestadores confiáveis, o agendamento, o histórico médico do pet e a compra de produtos — coisa que hoje nenhum concorrente entrega de forma integrada.

---

## 4. Outcomes e Métricas — North Star + Inputs

**North Star Metric (candidata) [HIPÓTESE]:**
> **Atendimentos concluídos com sucesso por mês via plataforma** (consulta, exame, banho/tosa ou pedido de produto que chega ao fim do ciclo com avaliação positiva ou reagendamento).

Justificativa: captura simultaneamente valor para tutor (recebeu o cuidado que buscava), para o prestador (monetizou a demanda) e para a plataforma (transação recorrente = retenção real, não vaidade de cadastro).

### Métricas de input por persona (que movem a North Star)

| Persona | Métrica de input | Por que importa |
|---|---|---|
| Tutor | Taxa de conversão busca → agendamento | Mede eficácia da descoberta/matching |
| Tutor | Taxa de retenção mensal (retorna em 60-90 dias) | Mede se o "cuidado contínuo" está funcionando |
| Clínica/Hospital | Taxa de ocupação da agenda | Mede se a demanda está preenchendo capacidade ociosa |
| Clínica/Hospital | Taxa de no-show | Mede eficácia de confirmação/lembretes |
| Pet Shop | Taxa de recompra (produtos recorrentes) | Mede fidelização via plataforma |
| Plataforma | GMV transacionado (serviços + produtos) | Mede tamanho do mercado capturado |
| Plataforma | NPS/rating médio dos prestadores | Mede se "confiança/reputação" está sendo entregue |
| B2B | Nº de parcerias entre clínicas ativadas | Mede tração do diferencial B2B |

**Métricas de guardrail:** tempo médio de resposta em emergências (não pode degradar ao escalar), taxa de churn de prestadores (não pode crescer GMV às custas de má experiência do lado da oferta).

---

## 5. Modelo de Negócio — Hipóteses de Monetização **[HIPÓTESE — não validado]**

| Fluxo de receita | Descrição | Quem paga |
|---|---|---|
| Comissão por agendamento concluído | % sobre o valor da consulta/exame/serviço realizado via plataforma | Clínica/Hospital |
| Comissão por venda de produto | % sobre GMV de e-commerce (ração, medicamento, acessórios) | Pet Shop |
| Assinatura SaaS (planos de listagem) | Plano free (listagem básica) vs. planos pagos (destaque em busca, analytics, mais membros de equipe) | Clínica/Hospital/Pet Shop |
| Taxa sobre transação B2B | % sobre volume transacionado entre clínicas parceiras (exames, insumos) | Clínica/Hospital |
| Ads / destaque de busca | Prestadores pagam para aparecer em posições de destaque nos resultados | Clínica/Hospital/Pet Shop |
| Fidelidade/cashback (fee de operação) | Taxa de operação do programa de fidelidade multi-prestador | Plataforma retém spread |

> Recomendação: validar com pesquisa de willingness-to-pay antes de comprometer roadmap de billing. Para o MVP, a hipótese mais barata de testar é comissão por agendamento (não exige billing recorrente).

---

## 6. Mapa de Features por Persona, Job e Prioridade

Modelo de priorização: **Now / Next / Later**, cada bloco amarrado ao outcome que ele move.

### 🟢 NOW (MVP — habilita a North Star Metric a existir)

| Feature (do escopo original) | Persona(s) | Job atendido | Outcome que move |
|---|---|---|---|
| Autenticação e Autorização (perfis, permissões, LGPD) | Todos | Base de confiança/segurança para qualquer transação | Guardrail de confiança |
| Cadastro de clínicas/pet shops/clientes/pets | Clínica, Pet Shop, Tutor | "Quero existir na plataforma" | Habilita oferta e demanda |
| Busca e filtros (especialidade, localização, preço, disponibilidade) | Tutor | "Quero achar rápido quem eu preciso" | Taxa de conversão busca → agendamento |
| Agendamento online + confirmação automática | Tutor, Clínica | "Quero marcar sem fricção" / "Quero reduzir no-show" | North Star + Taxa de ocupação/no-show |
| Carteira Digital do Pet (histórico básico) | Tutor, Veterinário | "Quero ter/ver o histórico sempre disponível" | Retenção do tutor |
| Avaliações e reputação (básico) | Tutor, Clínica | "Quero decidir com confiança" / "Quero ser reconhecida" | NPS/rating médio |

### 🟡 NEXT (Expansão — aumenta GMV e recorrência)

| Feature | Persona(s) | Job atendido | Outcome que move |
|---|---|---|---|
| Catálogo de produtos + compra direta (e-commerce) | Tutor, Pet Shop | "Quero comprar o que meu pet precisa sem sair do app" | GMV, recompra |
| Alertas/lembretes de vacinação e check-up | Tutor | "Quero não esquecer o que importa" | Retenção mensal |
| Telemedicina para triagem rápida | Tutor, Veterinário | "Quero uma resposta rápida sem sair de casa" | Conversão em emergências leves |
| Geolocalização para emergências 24h | Tutor | "Quero achar ajuda agora, perto de mim" | Guardrail de tempo de resposta em emergência |
| Programas de fidelidade/cashback | Tutor | "Quero ser recompensado por ser fiel" | Retenção, recompra |

### 🔴 LATER (Diferenciação e defensibilidade — depende de tração prévia)

| Feature | Persona(s) | Job atendido | Outcome que move |
|---|---|---|---|
| Integração B2B entre clínicas (parcerias em exames/cirurgias) | Clínica/Hospital | "Quero oferecer o que não tenho, colaborando" | Nº de parcerias B2B ativadas |
| Compra colaborativa de insumos entre clínicas | Clínica/Hospital | "Quero reduzir custo de insumos" | Retenção de prestadores |
| Marketplace único (serviços + produtos) como moat competitivo | Todos | Consolidação da jornada completa do pet | GMV + retenção combinados |

> **Nota de sequenciamento:** o bloco NOW é o menor conjunto de features que já permite medir a North Star Metric real com usuários reais. Antes de investir em NEXT/LATER, validar que o funil busca → agendamento → atendimento concluído → avaliação está de fato girando.

---

## 7. Diferenciais Competitivos (mantidos do escopo original, agora ligados a outcome)

- **Emergência 24h com geolocalização** → move o guardrail de tempo de resposta e é um forte gancho de aquisição/retenção do Tutor.
- **Programas de fidelidade e cashback** → move recompra e retenção.
- **Marketplace único (serviços médicos + produtos)** → é a tese central de defensibilidade: nenhum concorrente pontual (agenda-only ou e-commerce-only) cobre a jornada completa.

---

## 8. Riscos e Hipóteses a Validar

| Hipótese | Risco se estiver errada | Como validar |
|---|---|---|
| Tutores confiam o suficiente numa plataforma nova para agendar (vs. ligar direto) | Baixa conversão busca → agendamento | Teste com landing + agendamento manual assistido antes de construir tudo |
| Clínicas aceitam pagar comissão por agendamento | Lado da oferta não adota | Pesquisa de willingness-to-pay + piloto com 5-10 clínicas |
| North Star (atendimento concluído) é mensurável de forma confiável no MVP | Métrica de sucesso não reflete realidade | Definir evento de "conclusão" de forma inequívoca desde o design do agendamento |
| Emergência 24h é um driver real de aquisição (não só "nice to have") | Investimento em geolocalização/SLA sem retorno | Validar com pesquisa qualitativa e/ou dados de busca (ex: volume de buscas por "veterinário emergência perto de mim") |
| Modelo de comissão é sustentável frente a concorrentes que cobram assinatura fixa | Margem inviável ou fricção de preço com prestador | Modelar unit economics antes do lançamento comercial |

---

## 9. Próximos Passos Sugeridos

1. Validar personas e JTBD com 5-8 entrevistas reais (tutores) e 5-8 entrevistas com clínicas/pet shops.
2. Confirmar a North Star Metric e instrumentar o evento de "atendimento concluído" desde o design técnico.
3. Reduzir o bloco NOW a um MVP testável com o menor custo de construção possível.
4. Definir o modelo de monetização a testar no piloto (recomendação: comissão por agendamento, sem billing recorrente no dia 1).
5. Revisar este documento após o primeiro ciclo de validação — promover hipóteses **[HIPÓTESE]** confirmadas para "validado" ou descartá-las.
