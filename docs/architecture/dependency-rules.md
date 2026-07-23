# Dependency Rules

## Objetivo

Definir oficialmente as regras de dependência do projeto.

Estas regras são obrigatórias.

---

# Princípio Fundamental

As dependências apontam sempre para dentro do domínio.

Nunca o contrário.

---

# Fluxo Oficial

```text
Apps
    ↓

Application
    ↓

Domain

Infrastructure
    ↓

Domain
```

---

# Domain

O domínio não conhece:

- API
- HTTP
- Fastify
- Express
- Prisma
- Supabase
- PostgreSQL
- MongoDB
- Logger
- Config
- Filesystem

O domínio depende apenas de:

- TypeScript
- Shared Kernel
- Próprio domínio

---

# Application

Pode depender de:

- Domain

Não pode depender diretamente da infraestrutura.

---

# Infrastructure

Pode depender de:

- Domain
- Application

Nunca o contrário.

---

# Apps

As aplicações podem depender de:

- Application
- Domain
- Infrastructure
- Shared

---

# Dependências Proibidas

Nunca é permitido:

Domain → Infrastructure

Domain → API

Domain → Framework

Application → API

Application → Fastify

Application → Prisma

---

# Inversão de Dependência

Sempre que um Aggregate precisar de persistência, deverá depender de uma interface.

Nunca de uma implementação concreta.

---

# Shared

O package Shared contém apenas componentes técnicos.

Nunca poderá conter regras de negócio.

---

# Revisão

Todas as Pull Requests deverão verificar estas regras antes do merge.