# API Boundaries

Este documento define os limites entre os diferentes módulos do sistema.

Cada módulo comunica apenas através de contratos bem definidos.

---

# Objetivo

Garantir baixo acoplamento.

Evitar dependências cruzadas.

Permitir evolução independente.

---

# Contextos

## Wedding Planning

Responsável por:

- WeddingProject
- WeddingEvent
- WeddingStage

Não conhece detalhes de persistência.

---

## Participants

Responsável por:

- Participant
- ParticipantAssignment

---

## Needs

Responsável por:

- Need
- Need Templates
- Planning Engine

---

## Budget

Responsável por:

- Budget
- BudgetItem
- Estimativas

Nunca cria Needs.

Apenas reage a elas.

---

## Marketplace

Responsável por:

- Vendor
- VendorCategory
- VendorService

Não altera o domínio do casamento.

Apenas fornece soluções.

---

## Booking

Responsável por:

- ServiceBooking

Representa contratos entre casal e fornecedor.

---

## Analytics

Responsável por:

- indicadores
- estatísticas
- previsões

Nunca altera entidades do domínio.

É apenas consumidor de eventos.

---

# Comunicação

Preferencialmente:

Application Layer

↓

Repository Interfaces

↓

Domain Events

Evitar comunicação direta entre módulos.

---

# Dependências Permitidas

Planning

↓

Needs

↓

Budget

↓

Booking

↓

Analytics

Marketplace permanece independente.

---

# Regra

Um módulo nunca altera diretamente outro módulo.

Toda comunicação ocorre através de:

- Use Cases
- Repository Interfaces
- Domain Events