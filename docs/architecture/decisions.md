# Architecture Decisions

Este documento regista todas as decisões arquiteturais consideradas oficiais.

Sempre que uma decisão alterar o domínio, este documento deve ser atualizado.

---

# ADR-001

## Domain-Driven Design

**Decisão**

O projeto segue Domain-Driven Design.

**Motivo**

O problema é complexo e possui muitas regras de negócio.

---

# ADR-002

## Clean Architecture

O sistema segue uma arquitetura em camadas.

Frontend

↓

Application

↓

Domain

↓

Infrastructure

---

# ADR-003

## Rich Domain Model

Foi adotado um modelo rico mas pragmático.

As entidades encapsulam comportamento.

Domain Services existem apenas quando o comportamento não pertence naturalmente a nenhuma entidade.

---

# ADR-004

## Aggregate Root

WeddingProject é o Aggregate Root principal.

Nenhuma entidade externa modifica diretamente um agregado interno.

---

# ADR-005

## WeddingEvent

Representa um macro-acontecimento.

Exemplos:

- Lobolo
- Casamento
- Xiguiane
- After Party

Todo WeddingEvent possui pelo menos um WeddingStage.

---

# ADR-006

## WeddingStage

Representa uma unidade operacional.

Exemplos:

- Civil
- Religioso
- Receção

É o centro de:

- orçamento
- logística
- fornecedores
- necessidades
- cronograma

---

# ADR-007

## AgendaItem

AgendaItem representa apenas um ponto do cronograma.

Não possui:

- orçamento
- fornecedores
- convidados

Exemplos:

- Corte do bolo
- Primeira dança
- Entrada dos noivos

---

# ADR-008

## Need

Need representa uma decisão de planeamento.

É o elo entre:

Planeamento

↓

Orçamento

↓

Marketplace

↓

Contratação

---

# ADR-009

## ServiceBooking

ServiceBooking representa um compromisso comercial.

Nunca substitui a Need.

A Need continua a existir mesmo que o fornecedor seja alterado.

---

# ADR-010

## Vendor

Vendor representa uma empresa.

VendorService representa aquilo que essa empresa oferece.

As categorias classificam fornecedores.

VendorCategory

↓

Vendor

↓

VendorService

---

# ADR-011

## Planeamento

O sistema é orientado por necessidades.

O casal nunca começa escolhendo fornecedores.

Começa identificando necessidades.

---

# ADR-012

## Planning Engine

PlanningEngine é um Domain Service.

É responsável por gerar:

- Needs
- Tasks
- Estimativas

a partir de templates culturais.

---

# ADR-013

## Simplicidade

Sempre que existir conflito entre:

mais abstração

ou

mais simplicidade

escolhe-se simplicidade.