# Vendor

## Visão Geral

Vendor representa uma empresa ou profissional que disponibiliza serviços no marketplace do Os Padrinhos.

É um Aggregate Root independente.

Não conhece WeddingProjects.

Não conhece WeddingStages.

Não conhece Needs.

Apenas disponibiliza serviços ao marketplace.

---

# Responsabilidades

- representar um fornecedor;
- gerir os seus serviços;
- gerir disponibilidade;
- gerir informação pública;
- publicar alterações relevantes.

---

# Não é responsável por

- gerir casamentos;
- gerir bookings;
- calcular orçamentos;
- gerir pagamentos.

---

# Identidade

VendorId

Identificador único e imutável.

---

# Estrutura

Vendor

- VendorId
- BusinessInformation
- VendorCategory
- VendorServices
- Portfolio
- Contacts
- ServiceAreas
- Rating
- Status

---

# Invariantes

- pertence a uma VendorCategory;
- possui pelo menos um VendorService ativo;
- VendorId nunca muda.

---

# Comportamentos

- register()
- activate()
- deactivate()
- addService()
- removeService()
- updatePortfolio()
- updateContacts()

---

# Eventos de Domínio

- VendorRegistered
- VendorActivated
- VendorDeactivated
- VendorServiceAdded
- VendorServiceRemoved

---

# Relações

Vendor

↓

VendorServices

---

# Critérios de Aceitação

✓ representa uma empresa

✓ pode existir sem WeddingProjects

✓ pode existir sem Bookings

✓ possui catálogo próprio