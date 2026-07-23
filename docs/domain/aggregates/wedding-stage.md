# WeddingStage

## Visão Geral

WeddingStage representa uma fase operacional de um WeddingEvent.

É o verdadeiro centro operacional do domínio.

Exemplos:

Casamento

- Civil
- Religioso
- Receção

Lobolo

- Negociação
- Entrega
- Receção

---

# Responsabilidades

- gerir logística;
- gerir necessidades;
- gerir tarefas;
- gerir cronograma;
- gerir fornecedores contratados;
- gerir orçamento granular.

---

# Não é responsável por

- representar o casamento inteiro;
- gerir participantes globais;
- autenticação;
- pagamentos.

---

# Estrutura

WeddingStage

- StageId
- StageType
- Venue
- Schedule
- Needs
- Tasks
- BudgetItems
- VendorBookings
- ParticipantAssignments
- AgendaItems

---

# Invariantes

- pertence sempre a um WeddingEvent;
- possui Schedule válido;
- possui Venue válido;
- Needs nunca pertencem diretamente ao WeddingEvent.

---

# Regra de Herança

Participants pertencem ao WeddingEvent.

WeddingStage apenas define exceções através de ParticipantAssignments.

Na ausência de ParticipantAssignments utiliza automaticamente todos os participantes do WeddingEvent.

---

# Comportamentos

- rename()
- reschedule()
- changeVenue()
- addNeed()
- removeNeed()
- assignParticipant()
- removeParticipantAssignment()
- addTask()
- removeTask()
- addAgendaItem()

---

# Eventos de Domínio

- WeddingStageCreated
- WeddingStageRenamed
- NeedAdded
- NeedRemoved
- VenueChanged
- ScheduleChanged
- ParticipantAssigned

---

# Critérios de Aceitação

✓ representa uma unidade operacional

✓ é centro de custos

✓ é centro logístico

✓ possui Needs

✓ possui Tasks

✓ possui AgendaItems

✓ possui VendorBookings