# DOMAIN_ENTITIES.md

# Entidades do Domínio — Os Padrinhos

## Objetivo

Este documento traduz o modelo conceptual em entidades de domínio.

Não representa ainda tabelas de banco de dados.

Representa responsabilidades e comportamento.

---

# 1. WeddingProject

## Tipo

Aggregate Root principal.

## Responsabilidade

Representa todo o processo de planeamento.

## Dados principais

```text
id
status
coupleProfile
events[]
createdAt
updatedAt
```

## Estados

```text
DRAFT
PLANNING
CONFIRMED
COMPLETED
CANCELLED
```

## Regras

* Deve possuir um casal.
* Pode possuir vários WeddingEvents.
* Consolida informação financeira e operacional.

---

# 2. CoupleProfile

## Responsabilidade

Representa os noivos.

Não representa convidados.

## Dados

```text
partnerOne
partnerTwo
contactInformation
preferences
```

---

# 3. WeddingEvent

## Tipo

Aggregate.

## Responsabilidade

Representa um acontecimento macro.

Exemplos:

```text
CASAMENTO
LOBOLO
XIGUIANE
AFTER_PARTY
```

---

## Dados

```text
id
type
date
participants[]
stages[]
budgetSummary
status
```

---

## Regras

Obrigatório:

```text
WeddingEvent
    possui pelo menos um WeddingStage
```

---

# 4. Participant

## Responsabilidade

Pessoa relacionada com o evento.

Exemplos:

* convidado
* padrinho
* familiar
* fornecedor interno

---

## Dados

```text
id
name
contact
relationship
category
```

---

# 5. ParticipantAssignment

## Responsabilidade

Exceção de participação num Stage.

Normalmente não existe.

---

Exemplo:

Evento:

```text
Casamento
220 pessoas
```

Stage:

```text
Civil
```

Assignment:

```text
Pais
Irmãos
Padrinhos
```

---

# 6. WeddingStage

## Tipo

Aggregate operacional.

## Responsabilidade

Centro de execução e custos.

---

Exemplos:

```text
Civil
Religioso
Receção
Copo de Água
```

---

## Dados

```text
id
name
venue
schedule
needs[]
budgetItems[]
tasks[]
agendaItems[]
vendorBookings[]
```

---

## Regra principal

Tudo que gera custo ou decisão comercial deve estar aqui.

---

# 7. Need

## Tipo

Entidade central de decisão.

## Responsabilidade

Representa uma necessidade a resolver.

---

Exemplo:

```text
Need:

Fotografia

Categoria:
Photography

Stage:
Receção
```

---

## Dados

```text
id
name
category
priority
quantity
estimatedCost
status
```

---

# 8. BudgetItem

## Responsabilidade

Representa impacto financeiro.

---

Dados:

```text
id
description
estimatedAmount
actualAmount
paymentStatus
source
```

---

# 9. VendorCategory

## Responsabilidade

Classificação comercial.

Exemplos:

```text
Fotografia

Catering

Decoração

Música
```

---

# 10. Vendor

## Responsabilidade

Empresa ou profissional.

---

Dados:

```text
id
name
category
location
rating
```

---

# 11. VendorService

## Responsabilidade

Aquilo que realmente é comprado.

---

Exemplo:

Vendor:

```text
Studio XPTO
```

Serviços:

```text
Fotografia documental

Drone

Álbum premium
```

---

# 12. ServiceBooking

## Responsabilidade

Representa contratação.

Liga:

```text
Need

+

VendorService
```

---

Dados:

```text
vendorService
price
contractStatus
paymentTerms
```

---

# 13. AgendaItem

## Responsabilidade

Linha temporal simples.

---

Dados:

```text
time
title
description
```

---

Não possui:

* orçamento
* fornecedor
* participantes próprios

---

# 14. Task

## Responsabilidade

Ação operacional.

Exemplo:

```text
Confirmar decoração

Data limite:
10 Maio
```

---

# Relação final

```text
WeddingProject

 ├── CoupleProfile

 └── WeddingEvent

        ├── Participants

        └── WeddingStage

              ├── Need

              │     ├── BudgetItem
              │     └── ServiceBooking
              │
              ├── VendorBooking
              ├── Task
              └── AgendaItem
```
