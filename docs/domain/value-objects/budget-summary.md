# BudgetSummary

## Objetivo

Representa um resumo financeiro agregado.

Não armazena linhas individuais.

Resume o estado financeiro de um conjunto de BudgetItems.

---

## Atributos

- estimated
- contracted
- paid
- pending

---

## Responsabilidades

- consolidar valores
- calcular diferenças
- fornecer indicadores financeiros

---

## Operações

variance()

remaining()

completionPercentage()

---

## Invariantes

Nunca é editado manualmente.

É sempre derivado dos BudgetItems.

É imutável.

---

## Exemplo

Estimado

250 000 MZN

Contratado

245 000 MZN

Pago

180 000 MZN

Pendente

65 000 MZN
