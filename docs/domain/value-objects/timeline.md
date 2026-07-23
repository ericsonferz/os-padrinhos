# Timeline

## Objetivo

Representa uma sequência cronológica de AgendaItems.

Não substitui o Schedule.

Complementa-o.

---

## Utilizado por

WeddingStage

---

## Responsabilidades

- ordenar AgendaItems
- impedir conflitos
- calcular duração da etapa

---

## Operações

sort()

move()

validate()

duration()

---

## Invariantes

Os AgendaItems devem permanecer ordenados.

Não podem existir horários sobrepostos quando a regra do Stage não o permitir.

Timeline é imutável.
