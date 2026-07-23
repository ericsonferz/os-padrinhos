# Domain Enums

Este documento centraliza todos os Enumerations (Enums) utilizados pelo domínio do **Os Padrinhos**.

Os enums fazem parte da Linguagem Ubíqua do projeto e representam estados, classificações e comportamentos estáveis do negócio.

---

# WeddingProjectStatus

Representa o ciclo de vida do projeto.

```text
DRAFT
PLANNING
CONFIRMED
IN_PROGRESS
COMPLETED
CANCELLED
ARCHIVED
```

Utilizado por

- WeddingProject

---

# WeddingEventType

Representa os grandes acontecimentos do projeto.

```text
LOBOLO
WEDDING
XIGUIANE
AFTER_PARTY
BRUNCH
OTHER
```

Utilizado por

- WeddingEvent

---

# WeddingStageType

Representa as etapas operacionais de um WeddingEvent.

```text
CIVIL
RELIGIOUS
RECEPTION
TRADITIONAL
PHOTO_SESSION
DINNER
CEREMONY
OTHER
```

Utilizado por

- WeddingStage

---

# NeedPriority

```text
LOW
MEDIUM
HIGH
CRITICAL
```

Utilizado por

- Need

---

# NeedStatus

Estado genérico de evolução de uma Need.

Não representa workflow rígido.

```text
PENDING
ACTIVE
RESOLVED
CANCELLED
```

Utilizado por

- Need

---

# TaskStatus

```text
TODO
IN_PROGRESS
BLOCKED
COMPLETED
CANCELLED
```

Utilizado por

- Task

---

# TaskPriority

```text
LOW
MEDIUM
HIGH
URGENT
```

---

# BookingStatus

Representa o estado de uma contratação.

```text
DRAFT
PENDING
CONFIRMED
CANCELLED
COMPLETED
```

Utilizado por

- ServiceBooking

---

# PaymentStatus

```text
NOT_REQUIRED
PENDING
PARTIALLY_PAID
PAID
REFUNDED
```

Utilizado por

- BudgetItem
- ServiceBooking

---

# BudgetItemStatus

```text
ESTIMATED
QUOTED
APPROVED
CONTRACTED
PAID
CANCELLED
```

---

# ParticipantRole

Representa o papel de um participante.

```text
GUEST
BRIDE
GROOM
BEST_MAN
MAID_OF_HONOR
PARENT
CHILD
VENDOR
STAFF
OTHER
```

---

# RSVPStatus

```text
PENDING
CONFIRMED
DECLINED
MAYBE
```

---

# VendorStatus

```text
ACTIVE
INACTIVE
SUSPENDED
PENDING_APPROVAL
```

---

# VendorCategoryType

Categorias principais do Marketplace.

```text
PHOTOGRAPHY
VIDEOGRAPHY
MUSIC
CATERING
DECORATION
VENUE
FLOWERS
TRANSPORT
INVITATIONS
BEAUTY
SECURITY
ATTIRE
OTHER
```

---

# VendorServiceStatus

```text
ACTIVE
UNAVAILABLE
DISCONTINUED
```

---

# Currency

```text
MZN
USD
EUR
ZAR
```

---

# Language

```text
PT
EN
```

---

# NotificationChannel

```text
EMAIL
SMS
WHATSAPP
PUSH
```

---

# NotificationStatus

```text
PENDING
SENT
FAILED
READ
```

---

# ReminderType

```text
AUTOMATIC
MANUAL
SYSTEM
```

---

# RelationshipType

Representa relações entre participantes.

```text
FATHER
MOTHER
BROTHER
SISTER
UNCLE
AUNT
COUSIN
FRIEND
COLLEAGUE
OTHER
```

---

# VenueType

```text
CHURCH
REGISTRY
HOTEL
GARDEN
BEACH
HOME
RESTAURANT
HALL
OTHER
```

---

# PlanningSource

Origem de criação de uma Need.

```text
MANUAL
TEMPLATE
PLANNING_ENGINE
IMPORT
```

---

# DocumentType (Futuro)

```text
CONTRACT
INVOICE
RECEIPT
QUOTE
OTHER
```

---

# Design Principles

Os Enums representam conceitos estáveis do domínio.

Regras:

- evitar valores temporários;
- evitar enums dependentes da interface;
- evitar enums específicos da infraestrutura;
- cada enum deve existir apenas quando representa uma linguagem de negócio.
