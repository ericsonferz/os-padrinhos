# System Architecture

## Objetivo

Este documento descreve a arquitetura global do **Os Padrinhos**.

A arquitetura foi desenhada segundo os princípios de:

- Domain-Driven Design (DDD)
- Clean Architecture
- SOLID
- Rich Domain Model (Pragmático)
- Event-Driven (quando fizer sentido)

O domínio é o centro do sistema.

Toda a restante arquitetura existe para servir o domínio.

---

# Visão Geral

```
                Frontend
                    │
                    ▼
               HTTP / REST API
                    │
                    ▼
             Application Layer
                    │
                    ▼
              Domain Layer
                    │
                    ▼
         Infrastructure Layer
                    │
                    ▼
          Database / External APIs
```

As dependências apontam sempre para o domínio.

Nunca no sentido contrário.

---

# Camadas

## Domain

Representa o negócio.

Contém:

- Aggregates
- Entities
- Value Objects
- Domain Events
- Domain Services
- Repository Interfaces

Não conhece:

- HTTP
- Supabase
- PostgreSQL
- React
- Next.js

---

## Application

Coordena o domínio.

Contém:

- Use Cases
- Commands
- Queries
- DTOs

Não contém regras profundas de negócio.

---

## Infrastructure

Implementa detalhes técnicos.

Exemplos:

- Supabase
- PostgreSQL
- REST
- Storage
- Authentication

Pode depender do Domain.

O Domain nunca depende dela.

---

## Frontend

Interface do utilizador.

Responsável por:

- apresentação
- navegação
- estado da UI

Nunca implementa regras de negócio.

---

# Estrutura Geral

```
Frontend

↓

API

↓

Application

↓

Domain

↓

Infrastructure

↓

Database
```

---

# Filosofia

O sistema é construído de dentro para fora.

Primeiro:

Domínio.

Depois:

Aplicação.

Só no fim:

Infraestrutura e Interface.

---

# Bounded Contexts

O domínio encontra-se dividido em vários contextos.

- Wedding Planning
- Participants
- Budget
- Marketplace
- Vendors
- Analytics

Cada contexto possui responsabilidades próprias.

---

# Aggregate Root Principal

WeddingProject

É a porta de entrada do domínio.

Todos os restantes agregados vivem direta ou indiretamente ligados ao projeto.

---

# Agregados Principais

- WeddingProject
- WeddingEvent
- WeddingStage
- Participant
- Vendor
- Need
- ServiceBooking

---

# Domain Services

Exemplos:

PlanningEngine

BudgetEstimator

VendorMatcher

---

# Eventos de Domínio

Exemplos:

NeedCreated

NeedEstimated

VendorBooked

BudgetUpdated

WeddingStageCompleted

---

# Objetivo Final

Construir uma plataforma onde:

- o domínio controla o sistema;
- a infraestrutura é substituível;
- o código permanece simples;
- novas funcionalidades podem ser adicionadas sem comprometer a arquitetura.