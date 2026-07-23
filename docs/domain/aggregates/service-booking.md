# ServiceBooking

## Visão Geral

ServiceBooking representa o compromisso comercial entre uma Need e um VendorService.

É a concretização da decisão do casal.

Enquanto a Need representa uma intenção, o ServiceBooking representa uma contratação.

---

# Responsabilidades

- ligar Need a VendorService;
- manter histórico da contratação;
- representar compromisso comercial;
- acompanhar estado da contratação.

---

# Não é responsável por

- gerir pagamentos completos;
- representar contratos legais;
- gerir faturação.

Essas responsabilidades poderão existir em futuros Bounded Contexts.

---

# Identidade

BookingId

Único e imutável.

---

# Estrutura

ServiceBooking

- BookingId
- NeedId
- VendorId
- VendorServiceId
- AgreedPrice
- BookingStatus
- BookingDate
- Notes

---

# Estados

- Pending
- Confirmed
- Cancelled
- Completed

---

# Invariantes

- pertence sempre a uma Need;
- referencia exatamente um VendorService;
- o preço acordado nunca pode ser negativo.

---

# Comportamentos

- confirm()
- cancel()
- complete()
- changeNotes()

---

# Eventos de Domínio

- BookingCreated
- BookingConfirmed
- BookingCancelled
- BookingCompleted

---

# Relações

Need

↓

ServiceBooking

↓

VendorService

↓

Vendor

---

# Critérios de Aceitação

✓ representa uma contratação

✓ preserva histórico

✓ desacopla Need do Vendor

✓ suporta futuras integrações financeiras