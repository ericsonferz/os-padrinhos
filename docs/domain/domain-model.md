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
