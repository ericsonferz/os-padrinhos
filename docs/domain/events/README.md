# Domain Events

## Objetivo

Domain Events representam acontecimentos importantes ocorridos dentro do domínio.

Não representam ações da interface.

Representam factos.

Exemplos:

- WeddingProjectCreated
- WeddingEventCreated
- WeddingStageCreated
- NeedCreated
- NeedEstimated
- VendorBooked
- BudgetUpdated

## Regras

Todo Domain Event:

- aconteceu no passado;
- é imutável;
- possui timestamp;
- descreve apenas um facto.

Exemplo

NeedEstimated

Não significa:

"Estimar Need"

Significa:

"A Need foi estimada."

## Utilização futura

Estes eventos poderão alimentar:

- Analytics
- Notifications
- Emails
- Timeline
- Audit Log
- Integrações