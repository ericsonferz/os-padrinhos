# GuestCount

## Objetivo

Representa uma quantidade de convidados.

Evita utilizar números simples espalhados pelo domínio.

---

## Utilizado por

- WeddingEvent
- WeddingStage
- Simulation Engine

---

## Atributos

- total

---

## Responsabilidades

- representar capacidade
- comparar quantidades
- validar limites

---

## Operações

increase()

decrease()

equals()

isGreaterThan()

---

## Invariantes

Nunca pode assumir valores negativos.

Nunca pode ultrapassar limites definidos pela aplicação.

É imutável.

---

## Exemplos

120 convidados

250 convidados

35 convidados
