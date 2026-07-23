# Value Objects

## Objetivo

Os Value Objects representam conceitos do domínio que não possuem identidade própria.

Eles são definidos exclusivamente pelos seus valores e são imutáveis.

No domínio do Os Padrinhos, utilizamos Value Objects para evitar espalhar lógica simples por todo o sistema.

---

# Princípios

Um Value Object:

- não possui ID
- é imutável
- pode ser substituído por outro com o mesmo valor
- encapsula validações
- representa um conceito do negócio

---

# Lista Inicial

## Money

Representa um valor monetário.

Campos:

- amount
- currency

Exemplo

```
Money
├── amount
└── currency
```

Responsabilidades

- operações monetárias
- comparação
- arredondamento

---

## DateRange

Representa um intervalo temporal.

Campos

- startDate
- endDate

Utilizado em:

- WeddingEvent
- WeddingStage
- Booking

---

## Schedule

Representa um momento específico.

Campos

- date
- startTime
- endTime

Utilizado em:

- WeddingStage
- AgendaItem

---

## Address

Representa um local físico.

Campos

- country
- province
- city
- district
- neighborhood
- addressLine
- coordinates

Utilizado por:

- Venue
- Vendor

---

## Contact

Representa formas de contacto.

Campos

- phone
- email
- whatsapp

---

## PersonName

Representa o nome completo.

Campos

- firstName
- lastName
- displayName

---

## GuestCount

Representa quantidade de participantes.

Campos

- adults
- children

Métodos

- total()

---

## BudgetEstimate

Representa uma estimativa financeira.

Campos

- minimum
- expected
- maximum

Não representa um custo real.

Serve apenas para simulação.

---

# Evolução

Novos Value Objects surgirão conforme o domínio evoluir.

Exemplos futuros

- Percentage
- Rating
- Duration
- PaymentTerms
- GeoLocation
- PhoneNumber
- EmailAddress