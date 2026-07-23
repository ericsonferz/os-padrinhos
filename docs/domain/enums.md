# Domain Enums

## Objetivo

Os Enums representam estados controlados pelo domínio.

Devem conter apenas valores estáveis.

Nunca utilizar textos destinados à interface.

---

# WeddingProjectStatus

- Draft
- Planning
- Confirmed
- InProgress
- Completed
- Cancelled

---

# WeddingEventType

- Lobolo
- Wedding
- Xiguiane
- ReceptionOnly
- AfterParty
- Other

---

# WeddingStageType

- Civil
- Religious
- Reception
- Traditional
- Photos
- Other

---

# ParticipantRole

- Bride
- Groom
- Parent
- Sibling
- BestMan
- MaidOfHonor
- Guest
- Child
- VendorRepresentative

---

# NeedPriority

- Low
- Medium
- High
- Critical

---

# NeedStatus

Inicialmente apenas:

- Pending
- Active
- Completed
- Cancelled

Novos estados poderão surgir conforme o workflow amadurecer.

---

# BookingStatus

- Draft
- Requested
- Accepted
- Rejected
- Confirmed
- Cancelled
- Completed

---

# BudgetStatus

- Estimated
- Planned
- Approved
- Paid

---

# TaskStatus

- Todo
- InProgress
- Completed
- Cancelled

---

# VendorStatus

- PendingApproval
- Active
- Suspended
- Archived

---

# PaymentStatus

- Pending
- Partial
- Paid
- Overdue