# Participant

## Objetivo

Representa qualquer pessoa envolvida no casamento.

Não representa os noivos.

Pode representar:

- convidado
- padrinho
- madrinha
- familiar
- fornecedor convidado
- criança
- acompanhante

---

# Responsabilidades

- identidade
- contactos
- relações familiares
- RSVP
- etiquetas

---

# Não é responsável por

- decidir onde participa

Essa responsabilidade pertence ao ParticipantAssignment.

---

# Atributos

- id
- name
- contacts
- role
- tags
- notes

---

# Relacionamentos

WeddingEvent
    └── Participants

WeddingStage
    └── ParticipantAssignments
