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
