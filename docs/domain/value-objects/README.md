# Value Objects

## Objetivo

Value Objects representam conceitos do domínio que:

- não possuem identidade própria;
- são imutáveis;
- são comparados pelos seus valores;
- encapsulam regras de validação.

Exemplos:

- Money
- Address
- PhoneNumber
- Email
- Schedule
- DateRange
- VenueLocation

## Regras

Um Value Object:

- nunca possui ID;
- nunca existe sozinho;
- pertence sempre a uma Entity ou Aggregate;
- pode ser reutilizado em vários Aggregates.

## Exemplos

WeddingStage

├── Schedule
├── Venue
├── Money
└── Address

Participant

├── Email
├── PhoneNumber
└── Address

Vendor

├── Address
├── ContactInfo
└── BankAccount

## Princípios

- Imutáveis
- Sem efeitos colaterais
- Comparação por valor
- Reutilizáveis