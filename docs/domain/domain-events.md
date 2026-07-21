# Os Padrinhos — Domain Events

## Objetivo

Eventos de domínio representam acontecimentos importantes dentro do sistema.

Eles permitem comunicação entre módulos sem criar dependências diretas.

---

# WeddingProject Events

## WeddingProjectCreated

Quando:

Um novo projeto é criado.

Dados:

- projectId
- coupleId
- createdAt

---

## WeddingProjectCompleted

Quando:

O planeamento termina.

---

# WeddingEvent Events

## WeddingEventCreated

Quando:

Um novo evento é criado.

Exemplo:

Casamento

Lobolo

---

## WeddingStageCreated

Quando:

Uma nova fase operacional é criada.

Exemplo:

Receção

Civil

Religioso

---

# Planning Events

## PlanningStarted

Quando:

O casal inicia planeamento automático.

---

## NeedsGenerated

Quando:

Planning Engine cria necessidades.

Exemplo:

Receção gera:

- Catering
- DJ
- Decoração

---

# Need Events

## NeedCreated

Quando:

Uma nova necessidade aparece.

Dados:

- stageId
- category
- description

---

## NeedEstimated

Quando:

Sistema calcula valor estimado.

---

## NeedSubmittedForSourcing

Quando:

Casal procura fornecedores.

---

# Vendor Events

## VendorSelected

Quando:

Casal escolhe fornecedor.

---

# Booking Events

## ServiceBookingCreated

Quando:

Um serviço é contratado.

Dados:

- vendorId
- serviceId
- stageId
- amount

---

## ServiceBookingCancelled

Quando:

Contrato é cancelado.

---

# Budget Events

## BudgetItemCreated

Quando:

Uma necessidade gera impacto financeiro.

---

## PaymentRegistered

Quando:

Pagamento é registado.

---

# Completion Events

## WeddingStageCompleted

Quando:

Uma fase termina.

---

## WeddingEventCompleted

Quando:

Evento termina.

---

## WeddingProjectCompleted

Quando:

Todo o projeto termina.