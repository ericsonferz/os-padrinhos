# Need

## Visão Geral

Need representa uma necessidade real do casal.

É a unidade central de decisão do Os Padrinhos.

Todo o ecossistema gira à sua volta.

Planning

↓

Need

↓

Budget

↓

Marketplace

↓

Booking

---

# Responsabilidades

- representar uma necessidade;
- ligar planeamento ao orçamento;
- ligar orçamento ao marketplace;
- manter prioridade;
- manter estado;
- ligar categorias aos serviços.

---

# Não é responsável por

- contratar fornecedores;
- representar pagamentos;
- calcular orçamento global.

---

# Estrutura

Need

- NeedId
- Category
- Title
- Description
- Priority
- Status
- EstimatedBudget
- Metadata

---

# Estados

Não definir workflow rígido nesta fase.

Apenas:

- Draft
- Active
- Completed
- Cancelled

A evolução será refinada posteriormente.

---

# Invariantes

- pertence sempre a um WeddingStage;
- possui VendorCategory;
- nunca aponta diretamente para um Vendor.

---

# Fluxo Conceptual

Need

↓

VendorCategory

↓

VendorService

↓

ServiceBooking

---

# Comportamentos

- activate()
- complete()
- cancel()
- changePriority()
- changeCategory()
- estimateBudget()

---

# Eventos de Domínio

- NeedCreated
- NeedActivated
- NeedCompleted
- NeedCancelled
- NeedPriorityChanged
- NeedCategoryChanged

---

# Critérios de Aceitação

✓ representa uma decisão do casal

✓ não conhece fornecedores diretamente

✓ alimenta orçamento

✓ alimenta marketplace

✓ alimenta o simulador

✓ é independente da interface