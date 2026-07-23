# Folder Structure

A organização física do projeto reflete a arquitetura do domínio.

## Estrutura

```
backend/

domain/
    aggregates/
    entities/
    value-objects/
    events/
    services/
    repositories/
    enums/
    exceptions/

application/
    commands/
    queries/
    use-cases/
    dto/

infrastructure/
    database/
    persistence/
    repositories/
    http/
    auth/
    storage/

shared/
    types/
    utils/
    constants/

tests/

frontend/
```

## Regras

O domínio nunca depende de infrastructure.

Application depende apenas do Domain.

Infrastructure depende de Application e Domain.

Frontend comunica apenas através da API.

---

## Imports

Sempre preferir imports absolutos.

Evitar caminhos relativos longos.

Errado

```
../../../../domain
```

Correto

```
@domain
```