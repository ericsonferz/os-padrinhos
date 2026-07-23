# DateRange

## Objetivo

Representa um intervalo temporal.

É utilizado sempre que o domínio necessita representar um período e não apenas uma data.

---

## Utilizado por

- WeddingProject
- WeddingEvent
- WeddingStage
- VendorService (promoções)
- Contracts (futuro)

---

## Atributos

- startDate
- endDate

---

## Responsabilidades

- representar um intervalo
- calcular duração
- verificar sobreposição
- verificar inclusão de datas

---

## Operações

contains(date)

overlaps(range)

duration()

equals()

---

## Invariantes

- endDate nunca pode ser anterior a startDate
- DateRange é imutável
- duas instâncias são iguais apenas pelos seus valores

---

## Exemplos

Lobolo

12/08/2027

↓

12/08/2027

---

Casamento

20/08/2027

↓

21/08/2027
