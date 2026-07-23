# Enums

## Objetivo

Centralizar todas as enumerações utilizadas pelo domínio.

## Exemplos

WeddingProjectStatus

- Draft
- Planning
- Confirmed
- Completed
- Cancelled

WeddingEventType

- Wedding
- Lobolo
- Xiguiane
- AfterParty

WeddingStageType

- Civil
- Religious
- Reception
- Traditional
- Brunch

NeedPriority

- Low
- Medium
- High
- Critical

NeedStatus

- Draft
- Planned
- Estimated
- Active
- Completed
- Cancelled

BookingStatus

- Pending
- Confirmed
- Cancelled
- Completed

BudgetStatus

- Estimated
- Approved
- Contracted
- Paid

## Regra

Nunca utilizar strings mágicas.

Sempre utilizar enums do domínio.