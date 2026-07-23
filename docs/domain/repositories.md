# Repository Contracts

## Objetivo

Repositories representam a fronteira entre o domínio e a infraestrutura.

O domínio nunca conhece:

- SQL
- Supabase
- Prisma
- HTTP
- APIs

Ele conhece apenas contratos.

---

# WeddingProjectRepository

Responsabilidades

- save()
- update()
- findById()
- findBySlug()
- delete()

---

# WeddingEventRepository

Responsabilidades

- save()
- findByProject()
- update()

---

# WeddingStageRepository

Responsabilidades

- save()
- update()
- listByEvent()

---

# ParticipantRepository

Responsabilidades

- save()
- update()
- search()

---

# NeedRepository

Responsabilidades

- save()
- update()
- listByStage()

---

# VendorRepository

Responsabilidades

- save()
- search()
- listByCategory()

---

# VendorServiceRepository

Responsabilidades

- save()
- listByVendor()
- search()

---

# BookingRepository

Responsabilidades

- save()
- update()
- cancel()

---

# BudgetRepository

Responsabilidades

- save()
- update()

---

# Regras

Repositories nunca:

- executam regras de negócio
- calculam orçamento
- validam domínio
- tomam decisões

São apenas mecanismos de persistência.

---

# Implementações

Na infraestrutura existirão implementações como:

SupabaseWeddingProjectRepository

SupabaseNeedRepository

SupabaseVendorRepository

etc.

O domínio nunca conhece essas classes.

Depende apenas das interfaces.