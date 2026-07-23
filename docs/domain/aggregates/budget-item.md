# BudgetItem

## Objetivo

Representa uma linha financeira.

Não representa um orçamento completo.

Representa apenas um custo individual.

---

# Exemplos

- DJ

- Fotografia

- Catering

- Flores

- Transporte

---

# Responsabilidades

- valor estimado
- valor contratado
- valor pago
- categoria
- moeda

---

# Não é responsável por

- contratar fornecedores

- gerir pagamentos

---

# Atributos

- id
- title
- estimatedAmount
- contractedAmount
- paidAmount
- currency
- status

---

# Origem

Pode nascer de:

- Need

- criação manual

- template

- simulador

---

# Relacionamentos

WeddingStage
    └── BudgetItems

Need
    └── pode originar BudgetItem
