# WeddingEvent

## Visão Geral

WeddingEvent representa um grande acontecimento dentro de um WeddingProject.

Exemplos:

- Lobolo
- Casamento
- Xiguiane
- After Party
- Brunch

WeddingEvent não existe fora de um WeddingProject.

É uma Entity pertencente ao Aggregate WeddingProject.

---

# Responsabilidades

- representar um acontecimento do projeto;
- manter a lista principal de participantes;
- organizar WeddingStages;
- fornecer contexto para necessidades;
- agregar orçamento;
- publicar eventos relacionados com alterações do evento.

---

# Não é responsável por

- contratar fornecedores;
- gerir pagamentos;
- calcular orçamento detalhado;
- criar Needs;
- gerir AgendaItems.

---

# Identidade

EventId

Único dentro do WeddingProject.

---

# Estrutura

WeddingEvent

- EventId
- EventType
- Title
- Description
- DateRange
- Participants
- WeddingStages
- Metadata

---

# Invariantes

- pertence sempre a um WeddingProject;
- possui pelo menos um WeddingStage;
- possui lista principal de Participants;
- WeddingStages nunca existem órfãos.

---

# Comportamentos

- rename()
- schedule()
- reschedule()
- addParticipant()
- removeParticipant()
- addStage()
- removeStage()
- complete()
- cancel()

---

# Eventos de Domínio

- WeddingEventCreated
- WeddingEventRenamed
- WeddingStageAdded
- WeddingStageRemoved
- ParticipantAdded
- ParticipantRemoved
- WeddingEventCompleted
- WeddingEventCancelled

---

# Relações

WeddingProject

↓

WeddingEvent

↓

Participants

↓

WeddingStages

---

# Critérios de Aceitação

✓ pertence sempre a um WeddingProject

✓ possui pelo menos um WeddingStage

✓ controla a lista principal de participantes

✓ agrega orçamento

✓ não conhece Vendors nem Needs diretamente