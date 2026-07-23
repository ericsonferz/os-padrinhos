# Budget

## Objetivo

Representa uma visão agregada dos BudgetItems.

Não guarda valores próprios.

Calcula-os.

---

# Responsabilidades

- total estimado
- total contratado
- total pago
- total pendente

---

# Não guarda

Linhas financeiras.

Essas pertencem aos BudgetItems.

---

# Fontes

Σ BudgetItems

---

# Roll-up

Budget(Project)

↓

Σ Budget(Event)

↓

Σ Budget(Stage)

↓

Σ BudgetItems

---

# Regra

Budget é sempre derivado.

Nunca deve ser editado diretamente.
