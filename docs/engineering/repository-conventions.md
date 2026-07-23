# Repository Conventions

## Objetivo

Padronizar a organização e evolução do repositório.

---

# Organização

O repositório encontra-se dividido em:

- apps
- packages
- docs
- scripts
- tests
- tools

Cada diretório possui responsabilidade própria.

---

# Packages

Cada package representa uma camada arquitetural.

Não deverão existir packages genéricos.

---

# Nomenclatura

Pastas:

kebab-case

Exemplos:

budget-item

vendor-category

wedding-stage

---

Ficheiros:

PascalCase para classes.

Exemplo:

WeddingProject.ts

Budget.ts

Money.ts

---

Interfaces

Prefixo I NÃO é utilizado.

Exemplo:

Repository

PlanningService

BudgetPolicy

---

Enums

Sempre no singular.

Exemplo:

WeddingStatus

TaskPriority

NeedType

---

Value Objects

Representam conceitos do domínio.

Nunca são estruturas de dados genéricas.

---

# Imports

Preferimos imports explícitos.

Exemplo:

import { Entity } from "./Entity";

Evitar imports indiretos através de barrels internos.

---

# Index

Cada package possui apenas um index.ts público.

Pastas internas normalmente não possuem barrel.

---

# Commits

Commits devem representar uma alteração lógica.

Evitar commits gigantes.

---

# Branches

Cada funcionalidade deverá possuir branch própria.

---

# Pull Requests

Toda PR deverá:

- compilar
- passar testes
- respeitar arquitetura
- atualizar documentação quando necessário