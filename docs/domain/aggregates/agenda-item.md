# AgendaItem

## Objetivo

Representa um marco cronológico dentro de um WeddingStage.

Um AgendaItem não possui comportamento de negócio complexo.
O seu único propósito é organizar a sequência temporal das atividades que acontecem durante uma etapa do casamento.

---

# Exemplos

- Entrada dos Noivos
- Corte do Bolo
- Primeira Dança
- Lançamento do Bouquet
- Sessão de Fotos
- Brinde
- Abertura da Pista

---

# Responsabilidades

- definir um horário
- definir uma ordem cronológica
- fornecer contexto ao cronograma
- permitir notas ou instruções

---

# Não é responsável por

- orçamento
- fornecedores
- participantes
- necessidades
- pagamentos
- contratos

Esses elementos pertencem ao WeddingStage.

---

# Atributos

- id
- title
- description
- scheduledAt
- duration
- order
- notes

---

# Relacionamentos

WeddingStage
    └── AgendaItems

---

# Regras

AgendaItems nunca existem fora de um WeddingStage.

A alteração de AgendaItems nunca altera o orçamento.

AgendaItems nunca geram Needs automaticamente.

AgendaItems apenas organizam o cronograma operacional.

---

# Exemplos

Receção

├── Entrada dos Noivos
├── Primeira Dança
├── Corte do Bolo
├── Brinde
├── Sessão de Fotos
└── Abertura da Pista
