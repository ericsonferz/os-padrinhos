# Testing Strategy

## Prioridade

1. Domain
2. Application
3. Infrastructure
4. API
5. Frontend

---

## Domain

Testar:

- regras
- invariantes
- comportamento

Nunca testar getters.

---

## Domain Services

Devem possuir cobertura elevada.

Exemplo

PlanningEngine

BudgetEstimator

VendorMatcher

---

## Use Cases

Testar:

- fluxo
- erros
- integrações

---

## Infrastructure

Testar:

persistência

queries

mapeamentos

---

## UI

Testar apenas comportamento.

Evitar testes frágeis.

---

## Regra

Sempre que uma regra de negócio for criada,

deve existir pelo menos um teste que a valide.