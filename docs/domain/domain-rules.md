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