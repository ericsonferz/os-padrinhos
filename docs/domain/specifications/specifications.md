# Domain Specifications

## Objetivo

As Specifications representam regras de negócio reutilizáveis.

Elas respondem perguntas do tipo:

- Pode?
- Deve?
- É válido?
- Está autorizado?

Nunca modificam estado.

Nunca persistem dados.

Nunca executam comandos.

Apenas validam regras do domínio.

---

# Princípios

Uma Specification:

- possui um único objetivo;
- devolve verdadeiro ou falso;
- pode explicar porque falhou;
- pode ser combinada com outras Specifications.

---

# Organização

As Specifications serão agrupadas por Aggregate.

---

# WeddingProject

## CanCreateWeddingEventSpecification

### Objetivo

Verifica se um WeddingProject pode receber um novo WeddingEvent.

### Regras

- projeto não pode estar arquivado;
- projeto não pode estar cancelado.

---

## CanCloseWeddingProjectSpecification

### Objetivo

Verifica se um projeto pode ser concluído.

### Regras

- todos os WeddingEvents concluídos;
- nenhuma Need pendente;
- nenhuma Task crítica pendente.

---

# WeddingEvent

## EventMustContainStageSpecification

### Objetivo

Todo WeddingEvent deve possuir pelo menos um WeddingStage.

---

## EventParticipantsAreValidSpecification

Verifica se todos os participantes são válidos.

---

## EventCanBeCompletedSpecification

### Regras

Todos os Stages concluídos.

---

# WeddingStage

## StageRequiresVenueSpecification

### Objetivo

Determina se o tipo de Stage exige um Venue.

Exemplo

Civil

✔ Sim

Receção

✔ Sim

Sessão Fotográfica

Pode depender do contexto.

---

## StageRequiresScheduleSpecification

Todo Stage deve possuir Schedule válido.

---

## StageCanStartSpecification

Regras

- Venue definido;
- Schedule válido;
- Needs obrigatórias resolvidas.

---

## StageCanBeCompletedSpecification

Regras

- Tasks obrigatórias concluídas;
- Bookings obrigatórios concluídos.

---

# Need

## NeedRequiresBookingSpecification

Nem toda Need necessita de contratação.

Exemplo

Comprar alianças

✔ Não

Contratar fotógrafo

✔ Sim

---

## NeedCanBeResolvedSpecification

Regras

- Booking concluído

OU

- marcada como resolvida manualmente.

---

## NeedCanGenerateBudgetSpecification

Determina se uma Need deve criar BudgetItems.

---

# Budget

## BudgetCanBeApprovedSpecification

Regras

- nenhum BudgetItem inválido;
- valores consistentes.

---

## BudgetIsBalancedSpecification

Verifica consistência financeira.

---

# BudgetItem

## BudgetItemCanBePaidSpecification

Regras

- aprovado;
- contratado.

---

# Vendor

## VendorCanProvideNeedSpecification

Verifica se um Vendor possui um VendorService compatível.

---

## VendorCanBeBookedSpecification

Regras

- ativo;
- disponível.

---

# ServiceBooking

## BookingCanBeConfirmedSpecification

Regras

- Vendor ativo;
- Need válida;
- orçamento aprovado.

---

## BookingCanBeCancelledSpecification

Regras

- ainda não executado.

---

# Participant

## ParticipantCanAccessStageSpecification

Verifica se um participante pode participar num Stage.

Regra

Se existirem ParticipantAssignments,
usa-os.

Caso contrário,

herda Participants do WeddingEvent.

---

# Task

## TaskCanBeCompletedSpecification

Regras

- dependências concluídas;
- responsável definido.

---

# Planning Engine

## StageNeedsCanBeGeneratedSpecification

Verifica se o Planning Engine pode gerar Needs automaticamente.

Regras

- Stage válido;
- Template existente.

---

## TemplateIsCompatibleSpecification

Verifica compatibilidade entre

Template

↓

WeddingEvent

↓

WeddingStage.

---

# Composition

Specifications podem ser combinadas.

Exemplo

CanStartWeddingStage

=

StageRequiresVenue

AND

StageRequiresSchedule

AND

NeedsResolved

AND

RequiredBookingsCompleted

---

# Implementação

Cada Specification será implementada como uma classe independente.

Exemplo

CanBookVendorSpecification

↓

isSatisfiedBy(vendor, need): boolean

---

# Benefícios

- elimina ifs espalhados;
- reduz duplicação;
- facilita testes;
- mantém Aggregates pequenos;
- aumenta reutilização;
- melhora legibilidade.
