# Naming Conventions

## Classes

Sempre em PascalCase.

Exemplo

WeddingProject

Need

PlanningEngine

VendorBooking

---

## Interfaces

Não utilizar prefixo I.

Correto

WeddingRepository

Errado

IWeddingRepository

---

## Métodos

camelCase

confirmAttendance()

createNeed()

calculateEstimate()

---

## Booleanos

Sempre começar por:

is

has

can

should

Exemplo

isConfirmed

hasParticipants

canBookVendor

---

## Enums

PascalCase

WeddingStatus

NeedPriority

VendorCategory

---

## Eventos

Sempre no passado.

NeedCreated

VendorBooked

BudgetEstimated

WeddingStageCompleted

---

## Repositories

Sempre terminar em Repository.

NeedRepository

VendorRepository

WeddingProjectRepository

---

## Services

Devem representar conhecimento.

PlanningEngine

BudgetEstimator

VendorMatcher

Nunca:

Utils

Manager

Helper

Processor