# ARCHITECTURE.md

# Arquitetura Técnica — Os Padrinhos

## Objetivo

Definir a organização técnica inicial.

---

# Estilo Arquitetural

## Domain Driven Design (DDD)

Separação:

```text
Domain

Application

Infrastructure

Presentation
```

---

# Estrutura proposta

```text
src

├── domain

│   ├── wedding

│   ├── planning

│   ├── budgeting

│   ├── marketplace

│   └── shared


├── application

│   ├── use-cases

│   ├── commands
│   └── queries


├── infrastructure

│   ├── database
│   ├── repositories
│   └── external-services


└── presentation

    ├── api
    └── controllers
```

---

# Bounded Contexts

## 1. Planning Context

Responsável por:

* eventos
* stages
* necessidades
* tarefas

---

## 2. Budget Context

Responsável por:

* estimativas
* custos
* pagamentos

---

## 3. Marketplace Context

Responsável por:

* fornecedores
* serviços
* bookings

---

## 4. Analytics Context

Responsável por:

* dados históricos
* recomendações
* inteligência

---

# Domain Services

## PlanningEngine

Responsabilidade:

Gerar automaticamente:

* Needs
* Tasks
* Budget inicial

---

Exemplo:

Entrada:

```text
WeddingStage:
Receção
```

Saída:

```text
Needs:

Catering
DJ
Decoração
Fotografia
```

---

# Princípio de dependência

Regra:

```text
Application depende de Domain

Infrastructure depende de Application

Domain não depende de nada
```

---

# Repositórios

Interfaces vivem no domínio:

```text
WeddingProjectRepository

VendorRepository

BookingRepository
```

Implementações:

Infrastructure.

---

# Eventos de domínio futuros

Possíveis:

```text
WeddingCreated

StageCreated

NeedGenerated

BookingConfirmed

PaymentCompleted
```

---
