# Package Organization

## Objetivo

Definir a responsabilidade de cada package do projeto.

---

# application

Responsável pela orquestração dos casos de uso.

Contém:

- Use Cases
- DTOs
- Commands
- Queries
- Ports
- Mappers

Não contém regras de negócio.

---

# domain

É o coração do sistema.

Contém:

- Aggregates
- Entities
- Value Objects
- Policies
- Specifications
- Domain Services
- Events
- Exceptions
- Repositories (interfaces)
- Shared Kernel

Não conhece infraestrutura.

---

# infrastructure

Implementa detalhes técnicos.

Exemplos:

- Base de dados
- Repositórios concretos
- Serviços externos
- Configuração

Não contém regras de negócio.

---

# shared

Contém apenas componentes técnicos reutilizáveis.

Exemplos:

- Logger
- Config
- Validation
- Helpers

Não deve conter conceitos de domínio.

---

# Apps

As aplicações utilizam os packages.

Nunca implementam regras de negócio.

A API expõe casos de uso.

O Frontend consome casos de uso.

---

# Comunicação

Apps
↓

Application
↓

Domain

Infrastructure
↓

Domain

---

# Independência

Cada package deverá possuir:

- package.json
- tsconfig.json

A compilação deverá poder ocorrer individualmente.

---

# Evolução

Novos packages apenas poderão ser criados quando possuírem uma responsabilidade claramente definida.

Evitar packages genéricos.

A simplicidade é preferida à fragmentação excessiva.