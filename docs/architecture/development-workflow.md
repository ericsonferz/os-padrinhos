# Development Workflow

## Filosofia

O desenvolvimento do Os Padrinhos segue uma abordagem Domain First.

O código nunca começa pela interface nem pela base de dados.

A implementação segue sempre esta ordem.

---

# Ordem oficial

## 1. Domínio

Primeiro modelamos:

- Aggregate
- Entities
- Value Objects
- Domain Events
- Domain Services

Sem dependências externas.

---

## 2. Casos de Uso

Depois implementamos:

Application/

- Commands
- Queries
- Use Cases

Os casos de uso apenas coordenam o domínio.

---

## 3. Repositories

Depois definimos apenas as interfaces.

Exemplo

```
WeddingRepository
NeedRepository
VendorRepository
```

Sem implementação.

---

## 4. Infrastructure

Só depois implementamos:

- Supabase
- PostgreSQL
- REST
- APIs
- Storage

---

## 5. Frontend

A interface é sempre a última camada.

Nunca modelamos o domínio olhando para o UI.

---

# Fluxo para criar uma nova funcionalidade

Sempre seguir esta sequência:

1. Atualizar Domain Model
2. Atualizar Domain Rules
3. Criar Entidades
4. Criar Domain Service (se necessário)
5. Criar Use Case
6. Criar Repository Interface
7. Implementar Repository
8. Criar Endpoint
9. Criar Frontend

Nunca inverter esta ordem.

---

# Pull Requests

Um Pull Request deve conter apenas uma responsabilidade.

Exemplos:

✔ Criar Need

✔ Criar WeddingStage

✔ Criar PlanningEngine

Evitar PRs gigantes.

---

# Refatoração

É incentivada.

Mas nunca alterar o domínio sem atualizar a documentação.