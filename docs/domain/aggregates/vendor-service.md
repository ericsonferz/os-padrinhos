# VendorService

## Visão Geral

VendorService representa um serviço comercializado por um Vendor.

Exemplos:

- Fotografia
- Drone
- DJ
- Catering
- Open Bar
- Segurança
- Decoração

Não representa um fornecedor.

Representa aquilo que o fornecedor vende.

---

# Responsabilidades

- definir um serviço;
- definir preço base;
- definir disponibilidade;
- definir características.

---

# Estrutura

VendorService

- ServiceId
- Category
- Name
- Description
- BasePrice
- PricingModel
- Availability
- Tags

---

# Invariantes

- pertence sempre a um Vendor;
- possui VendorCategory;
- possui nome único dentro do Vendor.

---

# Comportamentos

- rename()
- activate()
- deactivate()
- updatePrice()
- updateAvailability()

---

# Eventos de Domínio

- VendorServiceCreated
- VendorServiceUpdated
- VendorServiceActivated
- VendorServiceDeactivated

---

# Relações

Vendor

↓

VendorService

---

# Critérios de Aceitação

✓ representa um serviço

✓ nunca representa uma empresa

✓ pode ser reutilizado em vários Bookings