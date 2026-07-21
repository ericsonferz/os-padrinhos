# Os Padrinhos — AI Knowledge Base

Version: 1.0.0
Last Updated: 2026-07-21
Status: Active

Purpose

This document consolidates the complete architecture, domain model,
business rules and product vision of Os Padrinhos.

It is intended to provide context to AI assistants
(ChatGPT, Claude, Gemini, Grok, Cursor, etc.).

This document is generated from the documentation under /docs.

If any conflict exists between this file and the source documents,
the source documents are the authoritative reference.

---

## Working Agreement

When assisting this project:

- Preserve the existing Domain Model.
- Do not introduce new entities without justification.
- Respect the Ubiquitous Language.
- Prefer extending existing concepts over creating parallel ones.
- Keep the architecture Domain-Driven.
- Avoid premature technical implementation decisions.
- Architectural decisions must be consistent with this document.

---

# architecture/architecture.md

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


---

# architecture/decisions.md

# DECISIONS.md

# Decisões Arquiteturais — Os Padrinhos

## Objetivo

Este documento regista as decisões fundamentais do domínio do Os Padrinhos.

Estas decisões devem ser consideradas a fonte de verdade antes de alterações estruturais no código.

---

# 1. Aggregate Root Principal

## Decisão

`WeddingProject` é o Aggregate Root principal do sistema.

## Responsabilidade

Representa o projeto completo de planeamento do casamento.

Inclui:

* casal
* eventos
* participantes globais
* estado do projeto
* visão consolidada financeira e operacional

Exemplo:

```
WeddingProject
João & Maria
2026
```

---

# 2. Separação entre Projeto, Evento e Stage

## Decisão

O domínio utiliza três níveis:

```
WeddingProject
    |
    WeddingEvent
        |
        WeddingStage
```

---

## WeddingProject

Representa o projeto completo.

Exemplo:

```
Casamento João + Maria
```

---

## WeddingEvent

Representa acontecimentos macro dentro do projeto.

Exemplos:

* Lobolo
* Casamento
* Xiguiane
* After Party

Cada evento possui:

* participantes principais
* orçamento agregado
* checklist
* stages

---

## WeddingStage

Representa uma unidade operacional com impacto real.

Exemplos:

* Civil
* Religioso
* Receção
* Copo de Água

Um Stage possui:

* local
* horário
* fornecedores
* necessidades
* orçamento
* tarefas

---

# 3. Regra de Peso do Domínio

Nem tudo no casamento é uma entidade.

## WeddingStage

Existe quando possui:

* regras próprias
* orçamento próprio
* fornecedores próprios
* local próprio
* impacto comercial

Exemplo:

```
Receção
DJ
Buffet
Decoração
Espaço
```

---

## AgendaItem

Existe quando é apenas um ponto cronológico.

Exemplo:

```
16:00 Entrada dos noivos
16:30 Corte do bolo
17:00 Primeira dança
```

Não possui:

* orçamento
* fornecedor
* convidados próprios

---

# 4. Participantes

## Decisão

Participantes pertencem ao WeddingEvent.

Não pertencem diretamente ao Stage.

Estrutura:

```
WeddingEvent
    |
    Participants
```

Por defeito:

```
Stage
    herda participantes do Event
```

---

## Exceções

Quando necessário:

```
ParticipantAssignments
```

Exemplo:

Civil:

* pais
* irmãos
* padrinhos

Receção:

* todos convidados

---

# 5. Need como unidade central

## Decisão

O sistema é orientado por necessidades, não por fornecedores.

Fluxo:

```
Need
 |
VendorCategory
 |
VendorService
 |
Vendor
 |
ServiceBooking
```

Exemplo:

Necessidade:

```
Precisamos de fotografia
```

Não:

```
Queremos contratar fotógrafo X
```

---

# 6. Vendor e VendorService

Fornecedor e serviço são conceitos separados.

Exemplo:

```
Vendor

Studio XPTO

    |
    Services

    Fotografia
    Drone
    Álbum
    Streaming
```

---

# 7. Orçamento

O orçamento nasce das necessidades.

Fluxo:

```
Need
 |
BudgetItem
 |
Stage Budget
 |
Event Budget
 |
Project Budget
```

O total é sempre uma agregação.

---

# 8. Planning Engine

O Planning Engine é um Domain Service.

Responsabilidade:

Transformar conhecimento cultural e operacional em:

* Needs
* Tasks
* BudgetItems preliminares

Exemplo:

Criar:

```
WeddingStage = Receção
```

gera:

```
Need:
- Catering
- Música
- Decoração
- Fotografia
- Segurança
```

---

# 9. Regra para implementação

Antes de criar novas entidades perguntar:

"Esta coisa possui comportamento próprio e impacto no negócio?"

Se não:

provavelmente é:

* atributo
* value object
* agenda item

e não uma entidade.


---

# architecture/api-boundaries.md

# Os Padrinhos — API Boundaries

## Objetivo

Definir fronteiras entre módulos e futuras APIs.

---

# Planning Context

Responsável por:

- WeddingProject
- WeddingEvent
- WeddingStage
- Needs

---

Endpoints futuros:

POST

/projects


GET

/projects/{id}


POST

/projects/{id}/events


POST

/events/{id}/stages


---

# Budget Context

Responsável por:

- Budget
- BudgetItems
- Estimates

Endpoints:

GET

/stages/{id}/budget


POST

/budget-items

---

# Marketplace Context

Responsável por:

- Vendors
- VendorServices
- Categories

Endpoints:

GET

/vendors

GET

/services


---

# Booking Context

Responsável por:

- Contratações
- Serviços reservados

Endpoints:

POST

/bookings


GET

/bookings/{id}


---

# Execution Context

Responsável por:

- Tasks
- Checklist
- Timeline

Endpoints:

POST

/tasks

PATCH

/tasks/{id}

---

# Analytics Context

Responsável por:

- métricas
- custos médios
- tendências

---

# domain/domain_model.md

DOMAIN_MODEL.md# DOMAIN_MODEL.md

# Modelo de Domínio — Os Padrinhos

## Linguagem Ubíqua

| Termo          | Significado                            |
| -------------- | -------------------------------------- |
| WeddingProject | Projeto completo do casamento          |
| WeddingEvent   | Grande acontecimento dentro do projeto |
| WeddingStage   | Unidade operacional e centro de custos |
| Need           | Necessidade que precisa ser resolvida  |
| Vendor         | Empresa/prestador                      |
| VendorService  | Serviço vendido pelo fornecedor        |
| ServiceBooking | Contratação efetiva                    |
| BudgetItem     | Linha financeira                       |
| AgendaItem     | Marco temporal simples                 |

---

# Modelo Geral

```
WeddingProject

├── CoupleProfile
│
├── WeddingEvents
│
│    └── WeddingEvent
│
│         ├── Participants
│         ├── Checklist
│         ├── Budget
│         │
│         └── WeddingStages
│
│              └── WeddingStage
│
│                   ├── Venue
│                   ├── Schedule
│                   ├── Needs
│                   ├── BudgetItems
│                   ├── VendorBookings
│                   ├── ParticipantAssignments
│                   ├── Tasks
│                   └── AgendaItems
│
├── Vendors
│
└── Analytics
```

---

# WeddingProject

Responsabilidade:

Controla o ciclo de vida geral.

Estados possíveis:

```
DRAFT
PLANNING
CONFIRMED
COMPLETED
```

---

# WeddingEvent

Representa:

* Lobolo
* Casamento
* Xiguiane
* After Party

Exemplo:

```
WeddingEvent:

type:
CASAMENTO

participants:
220 pessoas
```

---

# WeddingStage

Centro operacional.

Exemplo:

```
WeddingStage:

Receção

Venue:
Salão X

Needs:
Buffet
DJ
Decoração

Budget:
500.000 MT
```

---

# Need

A entidade mais importante para inteligência do produto.

Representa:

"Algo que precisamos resolver."

Exemplo:

```
Need

name:
Fotografia

stage:
Receção

priority:
HIGH
```

Pode evoluir:

```
Identificada

↓

Estimativa criada

↓

Em procura

↓

Contratada

↓

Executada
```

---

# ServiceBooking

Representa o compromisso comercial.

Liga:

```
Need

+

VendorService

=

Booking
```

Exemplo:

```
Need:
Fotografia

Vendor:
Studio XPTO

Service:
Fotografia documental

Booking:
Contrato confirmado
```

---

# Vendor

Representa o fornecedor.

Exemplo:

```
Vendor:

Studio XPTO

Category:

Photography
```

---

# VendorService

Representa aquilo que é comprado.

Exemplo:

```
Fotografia documental

Drone

Álbum premium

Live streaming
```

---

# AgendaItem

Elemento simples.

Exemplo:

```
AgendaItem

time:
16:30

title:
Corte do bolo
```

Não possui lógica comercial.


---

# domain/domain_entities.md

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


---

# domain/domain_rules.md

# Os Padrinhos — Domain Rules

## Objetivo

Este documento define as regras de negócio fundamentais do domínio.

Estas regras representam invariantes do sistema e devem ser respeitadas independentemente da interface, API ou implementação técnica.

---

# 1. WeddingProject Rules

## Rule WP-001 — Projeto pertence ao casal

Todo WeddingProject deve possuir um CoupleProfile.

Um projeto não existe sem identificar o casal responsável.

---

## Rule WP-002 — Projeto pode possuir múltiplos eventos

Um WeddingProject pode conter vários WeddingEvents.

Exemplo:

WeddingProject

- Lobolo
- Casamento
- Xiguiane
- After Party

---

# 2. WeddingEvent Rules

## Rule WE-001 — Todo evento precisa de pelo menos um Stage

Um WeddingEvent nunca existe sem uma unidade operacional.

Exemplo:

Lobolo simples:

WeddingEvent

↓

WeddingStage:
"Lobolo"

Motivo:

Todo planeamento, custo e execução acontecem ao nível do Stage.

---

## Rule WE-002 — Participantes pertencem ao Evento

A lista principal de participantes pertence ao WeddingEvent.

Não pertence ao Stage.

Exemplo:

Casamento:

220 convidados

↓

Civil
Religioso
Receção

Todos herdam essa lista.

---

## Rule WE-003 — Stage pode restringir participantes

Por defeito:

WeddingStage herda todos os participantes do evento.

Caso exista ParticipantAssignment:

o Stage utiliza apenas os participantes atribuídos.

Exemplo:

Evento:

220 convidados

Civil:

Pais + irmãos + padrinhos

---

# 3. WeddingStage Rules

## Rule WS-001 — Stage é unidade operacional

Toda operação do casamento acontece num Stage.

Inclui:

- local
- horário
- necessidades
- fornecedores
- custos
- tarefas

---

## Rule WS-002 — Custos pertencem ao Stage

Todo custo operacional deve estar associado ao Stage onde acontece.

Exemplo:

DJ:

Receção

não:

Casamento inteiro.

---

## Rule WS-003 — Stage possui AgendaItems

AgendaItems representam momentos cronológicos.

Exemplo:

- Entrada dos noivos
- Corte do bolo
- Primeira dança

AgendaItem não possui:

- orçamento próprio
- fornecedor próprio
- participantes próprios

---

# 4. Need Rules

## Rule ND-001 — Need representa intenção

Need representa uma necessidade do casal.

Exemplo:

"Precisamos de fotografia"

Não representa ainda um fornecedor.

---

## Rule ND-002 — Need pertence ao Stage

Toda necessidade nasce dentro de um contexto operacional.

Exemplo:

Receção:

Need:
DJ

---

## Rule ND-003 — Need não conhece Vendor diretamente

Fluxo obrigatório:

Need

↓

VendorCategory

↓

VendorService

↓

Vendor

↓

Booking

---

# 5. Vendor Rules

## Rule VN-001 — Vendor e Service são conceitos diferentes

Um fornecedor pode possuir vários serviços.

Exemplo:

Fornecedor:

Studio X

Serviços:

- Fotografia
- Vídeo
- Drone

---

# 6. Booking Rules

## Rule BK-001 — Booking representa compromisso

Booking só existe quando existe uma decisão comercial.

---

## Rule BK-002 — Booking não elimina Need

A necessidade permanece como histórico.

Exemplo:

Need:

Fotografia

Booking:

Studio Carlos

---

# 7. Budget Rules

## Rule BG-001 — Budget nasce das decisões

O orçamento é consequência das Needs.

Fluxo:

Need

↓

BudgetItem

↓

Budget

---

## Rule BG-002 — Valores evoluem

Um BudgetItem pode passar por:

Estimado

Cotado

Contratado

Pago

---

# 8. Planning Engine Rules

## Rule PE-001

Planning Engine pode criar Needs automaticamente.

Base:

- tipo de evento
- tipo de stage
- cultura
- número de convidados

---

## Rule PE-002

Sugestões automáticas nunca substituem decisão humana.

O casal confirma necessidades geradas.

---

# domain/domain_events.md

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

---

# domain/domain_services.md

# Os Padrinhos — Domain Services

## Objetivo

Domain Services representam lógica que não pertence naturalmente a uma entidade específica.

---

# 1. PlanningEngine

## Responsabilidade

Gerar automaticamente estrutura inicial de planeamento.

Entrada:

- WeddingEvent
- WeddingStage
- cultura
- localização
- convidados

Saída:

- Needs
- Tasks
- Budget estimado

---

Exemplo:

Entrada:

WeddingStage:

Receção

300 convidados


Saída:

Needs:

- Catering
- DJ
- Decoração
- Fotografia
- Segurança

---

# 2. SimulationEngine

## Responsabilidade

Estimar custos.

Base:

- categoria
- localização
- número de convidados
- mercado

Saída:

Intervalos de preço.

Exemplo:

Fotografia:

15.000 - 35.000 MT

---

# 3. RecommendationEngine

## Responsabilidade

Recomendar fornecedores.

Critérios:

- categoria
- orçamento
- localização
- disponibilidade
- avaliação

---

# 4. BudgetCalculationService

## Responsabilidade

Consolidar valores.

Fluxo:

Stage Budget

↓

Event Budget

↓

Project Budget

---

# 5. VendorMatchingService

## Responsabilidade

Encontrar serviços adequados para uma Need.

Fluxo:

Need

↓

Category

↓

VendorService

↓

Vendor

---

# domain/domain-context-map.md

# Domain Context Map

## Objetivo

Este documento define os Bounded Contexts do **Os Padrinhos**, as respetivas responsabilidades e a forma como se relacionam.

O objetivo é evitar acoplamento excessivo entre módulos e manter o domínio organizado à medida que o sistema evolui.

---

# Contextos

Wedding Project
│
├── Planning
├── Participants
├── Budget
├── Marketplace
├── Booking
├── Execution
└── Analytics

---

## 1. Planning Context

Responsável pelo planeamento do casamento.

Entidades principais:

- WeddingProject
- WeddingEvent
- WeddingStage
- Need
- Task
- AgendaItem

Responsabilidades:

- organização do projeto
- criação dos eventos
- criação dos stages
- geração de necessidades
- planeamento

Não conhece pagamentos nem contratos.

---

## 2. Participants Context

Responsável pelas pessoas.

Entidades:

- Participant
- ParticipantAssignment
- CoupleProfile

Responsabilidades:

- convidados
- padrinhos
- familiares
- fornecedores convidados
- confirmação de presença

---

## 3. Budget Context

Responsável pelo domínio financeiro.

Entidades:

- Budget
- BudgetItem

Responsabilidades:

- estimativas
- orçamento previsto
- orçamento contratado
- pagamentos futuros

Não conhece fornecedores diretamente.

Recebe informação do Planning.

---

## 4. Marketplace Context

Responsável pela oferta existente.

Entidades:

- VendorCategory
- Vendor
- VendorService

Responsabilidades:

- catálogo
- pesquisa
- filtros
- avaliações
- disponibilidade

Não conhece projetos específicos.

---

## 5. Booking Context

Responsável pela contratação.

Entidades:

- ServiceBooking

Responsabilidades:

- contratação
- negociação
- cancelamento
- alteração

Liga Planning ao Marketplace.

---

## 6. Execution Context

Responsável pelo acompanhamento do casamento.

Entidades:

- Checklist
- Tasks
- AgendaItem

Responsabilidades:

- execução
- acompanhamento
- progresso

---

## 7. Analytics Context

Responsável pelos dados agregados.

Exemplos:

- custo médio de receções
- fornecedores mais contratados
- necessidades mais frequentes
- tendências

Não altera dados operacionais.

Apenas consulta.

---

# Fluxo principal

WeddingProject
        │
        ▼
Planning
        │
        ▼
Need
        │
        ├────────► Budget
        │
        ├────────► Marketplace
        │
        ▼
ServiceBooking
        │
        ▼
Execution
        │
        ▼
Analytics

---

# Dependências

Planning
    ↓
Budget

Planning
    ↓
Marketplace

Marketplace
    ↓
Booking

Booking
    ↓
Execution

Execution
    ↓
Analytics

Nunca no sentido inverso.

Os contextos superiores não conhecem detalhes dos inferiores.


---

# domain/ubiquitous-language.md

# Os Padrinhos — Ubiquitous Language

## Objetivo

Este documento define o vocabulário oficial do domínio.

Todos os membros da equipa devem usar estes termos.

---

# WeddingProject

Definição:

Projeto completo de planeamento de casamento de um casal.

---

# WeddingEvent

Definição:

Grande acontecimento dentro do projeto.

Exemplos:

- Lobolo
- Casamento
- Xiguiane

---

# WeddingStage

Definição:

Unidade operacional dentro de um evento.

Possui:

- local
- custos
- fornecedores
- necessidades

Exemplos:

- Civil
- Religioso
- Receção

---

# AgendaItem

Definição:

Elemento simples do cronograma.

Exemplos:

- Corte do bolo
- Primeira dança

Não possui custo próprio.

---

# Participant

Definição:

Pessoa ligada ao projeto.

Pode ser:

- convidado
- familiar
- padrinho
- testemunha

---

# Need

Definição:

Problema ou necessidade que precisa ser resolvida.

Exemplo:

"Precisamos de música"

---

# VendorCategory

Definição:

Grupo de serviços.

Exemplos:

- Fotografia
- Catering
- Música

---

# Vendor

Definição:

Empresa ou profissional que fornece serviços.

---

# VendorService

Definição:

Oferta específica de um fornecedor.

Exemplo:

Vendor:

Studio X

Service:

Fotografia documental

---

# Booking

Definição:

Compromisso comercial entre casal e fornecedor.

---

# BudgetItem

Definição:

Representação financeira de uma necessidade.

---

# PlanningEngine

Definição:

Serviço inteligente que sugere estrutura de planeamento.

---

# SimulationEngine

Definição:

Serviço que estima custos com base no mercado.

---

# Marketplace

Definição:

Camada onde necessidades encontram fornecedores.

---

# product/vision.md

# Visão do Produto — Os Padrinhos

> Versão: 1.0
> Estado: Aprovado
> Objetivo: Definir a visão, missão e princípios orientadores do domínio.

---

# O que é o Os Padrinhos?

**Os Padrinhos** é uma plataforma digital de planeamento e gestão de casamentos, concebida para acompanhar o casal desde a primeira ideia até à conclusão de todos os eventos que fazem parte da celebração.

Mais do que um organizador de tarefas ou um marketplace de fornecedores, o sistema funciona como um assistente inteligente de planeamento, ajudando o casal a tomar decisões, estimar custos, organizar participantes, contratar serviços e acompanhar toda a execução do projeto.

O domínio foi concebido para refletir a realidade cultural e operacional dos casamentos em Moçambique, mantendo flexibilidade para acomodar diferentes tradições, estilos e formatos de celebração.

---

# Missão

Simplificar o planeamento de casamentos através de uma plataforma que transforma decisões complexas em processos organizados, previsíveis e colaborativos.

---

# Visão

Ser a plataforma de referência para o planeamento de casamentos em Moçambique e, futuramente, noutros mercados africanos, integrando planeamento, orçamento, fornecedores e execução numa única experiência.

---

# O Problema que Resolvemos

O planeamento de um casamento envolve dezenas de decisões, centenas de tarefas e múltiplos intervenientes.

Na prática, os casais recorrem frequentemente a folhas de cálculo, grupos de WhatsApp, cadernos, documentos dispersos e contactos informais de fornecedores.

Esta fragmentação provoca:

- perda de informação;
- dificuldade em controlar o orçamento;
- falta de organização;
- decisões pouco informadas;
- dificuldade em comparar fornecedores;
- pouca previsibilidade dos custos.

O Os Padrinhos procura eliminar essa fragmentação através de um único sistema integrado.

---

# Princípios Fundamentais

## 1. O casamento é um projeto

O casamento é tratado como um projeto com objetivos, orçamento, participantes, fases e resultados.

Todo o sistema organiza-se em torno do `WeddingProject`.

---

## 2. O planeamento é orientado por decisões

O centro do domínio não são os fornecedores.

Também não são os eventos.

O centro do domínio são as necessidades reais do casal.

Cada decisão de planeamento origina novas necessidades que alimentam o restante sistema.

---

## 3. As necessidades ligam todo o domínio

Uma necessidade pode originar:

- estimativas de custo;
- tarefas;
- procura de fornecedores;
- contratação de serviços;
- acompanhamento da execução.

A entidade `Need` constitui o fio condutor entre os diferentes módulos da plataforma.

---

## 4. A tecnologia adapta-se ao casamento

O sistema não obriga o casal a seguir um modelo rígido.

Cada projeto pode representar diferentes tradições, culturas e formatos de celebração.

Exemplos:

- casamento civil;
- casamento religioso;
- lobolo;
- xiguiane;
- receção;
- after party;
- brunch;
- outros eventos relevantes.

---

## 5. O domínio representa a realidade

As entidades existem porque representam conceitos reais do negócio.

Não são criadas por conveniência técnica.

Cada entidade deve possuir responsabilidades claras e significado para o utilizador.

---

## 6. A simplicidade é uma prioridade

O utilizador não deve ser exposto à complexidade interna do domínio.

O sistema deve automatizar sempre que possível:

- criação de necessidades;
- checklists;
- estimativas iniciais;
- sugestões de fornecedores;
- organização da informação.

---

# Os Pilares do Produto

O produto assenta sobre cinco pilares principais.

## Planeamento

Organização dos eventos, etapas, tarefas e necessidades.

---

## Orçamento

Estimativa, acompanhamento e controlo financeiro do projeto.

---

## Marketplace

Descoberta, comparação e contratação de fornecedores e respetivos serviços.

---

## Execução

Acompanhamento da preparação e realização dos eventos.

---

## Analytics

Transformação dos dados do projeto em informação útil para apoiar decisões futuras.

---

# O que o sistema NÃO é

O Os Padrinhos não é apenas:

- uma agenda;
- uma checklist;
- um marketplace;
- um gestor financeiro.

É uma plataforma integrada de planeamento de casamentos.

---

# Filosofia Arquitetural

O domínio é desenvolvido segundo princípios de Domain-Driven Design (DDD).

As decisões de negócio têm prioridade sobre decisões técnicas.

A arquitetura procura garantir:

- elevada coesão;
- baixo acoplamento;
- linguagem ubíqua consistente;
- evolução incremental;
- facilidade de manutenção.

---

# Critério de Evolução

Novas funcionalidades só devem ser introduzidas quando reforçarem esta visão.

Se uma funcionalidade obrigar a quebrar os princípios definidos neste documento, o domínio deve ser revisto antes da implementação.

---

# Estado

Este documento constitui a visão oficial da versão inicial do domínio do projeto Os Padrinhos.

---

# product/use_cases.md

# USE_CASES.md

# Casos de Uso Principais — Os Padrinhos

---

# UC01 — Criar Projeto de Casamento

## Ator

Casal

## Fluxo

1. Criar WeddingProject
2. Definir CoupleProfile
3. Escolher tipo de casamento
4. Criar eventos iniciais

Resultado:

```
WeddingProject criado
```

---

# UC02 — Criar Evento

Exemplo:

Criar:

```
WeddingEvent

CASAMENTO
```

ou:

```
WeddingEvent

LOBOLO
```

Sistema cria estrutura base.

---

# UC03 — Adicionar Stage

Exemplo:

Adicionar:

```
WeddingStage

Receção
```

Sistema solicita:

* local
* data
* horário

Depois pode gerar necessidades.

---

# UC04 — Gerar Planeamento Automático

Actor:

Planning Engine

Entrada:

```
WeddingStage:
Receção
```

Resultado:

```
Needs:

Catering
DJ
Decoração
Fotografia
Segurança
```

---

# UC05 — Estimar Orçamento

Sistema analisa:

* tipo de stage
* número de convidados
* localização
* dados históricos

Cria:

```
BudgetItems
```

Exemplo:

```
Buffet

Estimativa:
350.000 MT
```

---

# UC06 — Procurar Fornecedor

Entrada:

```
Need:

Fotografia
```

Sistema:

1. identifica categoria
2. procura VendorServices
3. apresenta fornecedores compatíveis

---

# UC07 — Contratar Serviço

Fluxo:

```
Need

↓

VendorService

↓

ServiceBooking
```

Atualiza:

* orçamento
* estado operacional
* histórico

---

# UC08 — Gerir Participantes

Adicionar:

```
Participant

Maria da Silva
```

ao:

```
WeddingEvent
```

Automaticamente disponível nos Stages.

Caso especial:

Criar:

```
ParticipantAssignment
```

para restringir presença.

---

# UC09 — Executar Evento

Durante o casamento:

Sistema acompanha:

* tarefas
* pagamentos
* fornecedores
* agenda

---

# UC10 — Pós-evento

Dados reais alimentam:

* analytics
* preços médios
* recomendações futuras
* inteligência do Planning Engine

---

# Princípio geral

O Os Padrinhos não começa pelo fornecedor.

Começa pela pergunta:

"Que necessidade existe neste momento do casamento?"

A partir daí:

```
Necessidade

↓

Planeamento

↓

Orçamento

↓

Fornecedor

↓

Execução
```


---

# product/implementation_roadmap.md

# IMPLEMENTATION_ROADMAP.md

# Plano de Implementação — Os Padrinhos

## Objetivo

Construir o sistema em ordem correta.

---

# Fase 1 — Fundação do Domínio

Criar:

```text
WeddingProject

WeddingEvent

WeddingStage

Participant
```

Objetivo:

Ter o núcleo do planeamento.

---

# Fase 2 — Planeamento Inteligente

Criar:

```text
Need

PlanningEngine

Task
```

Objetivo:

Transformar tipos de casamento em necessidades.

---

Exemplo:

Entrada:

```text
Casamento tradicional
```

Resultado:

```text
Needs:

Buffet

Decoração

Fotografia

Música
```

---

# Fase 3 — Orçamento

Criar:

```text
BudgetItem

BudgetCalculator
```

Objetivo:

Transformar necessidades em previsão financeira.

---

# Fase 4 — Marketplace

Criar:

```text
VendorCategory

Vendor

VendorService

ServiceBooking
```

Objetivo:

Conectar necessidades a fornecedores.

---

# Fase 5 — Execução

Criar:

```text
Tasks

Agenda

Payments
```

Objetivo:

Acompanhar preparação real.

---

# Fase 6 — Inteligência

Criar:

```text
Analytics

Recommendation Engine

Market Insights
```

---

# Ordem recomendada no Cursor

Executar nesta sequência:

1.

```text
/domain/entities
```

2.

```text
/domain/value-objects
```

3.

```text
/domain/services
```

4.

```text
/application/use-cases
```

5.

```text
/infrastructure
```

6.

```text
/api
```

---

# Regra de ouro

Não criar:

* pagamentos
* contratos
* notificações
* marketplace completo

antes do domínio base funcionar.

Primeiro:

```text
Planeamento

↓

Necessidade

↓

Orçamento

↓

Fornecedor

↓

Execução
```

Essa é a espinha dorsal do produto.
