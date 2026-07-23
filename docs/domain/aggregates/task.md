# Task

## Objetivo

Representa uma ação concreta que deve ser executada.

Exemplos:

- reservar igreja
- pagar fotógrafo
- confirmar DJ
- experimentar vestido

---

# Responsabilidades

- descrição
- prioridade
- responsável
- prazo
- estado

---

# Não é responsável por

- gerar Needs
- gerir orçamento

---

# Atributos

- id
- title
- description
- dueDate
- priority
- status
- assignee

---

# Relacionamentos

WeddingStage
    └── Tasks

Need
    └── pode gerar Tasks

PlanningEngine
    └── pode criar Tasks automaticamente
