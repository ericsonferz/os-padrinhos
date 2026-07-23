# Monorepo Strategy

## Objetivo

Definir oficialmente a estratégia de organização do código do projeto.

---

# Filosofia

O projeto utiliza uma arquitetura baseada em Monorepo.

Todos os componentes relacionados pertencem ao mesmo repositório.

---

# Objetivos

- reutilização de código
- consistência arquitetural
- versionamento único
- simplificação do desenvolvimento
- facilidade de auditoria

---

# Organização

```text
apps/

packages/

docs/

tests/

scripts/
```

---

# Apps

Contêm aplicações executáveis.

Cada aplicação possui autonomia.

Exemplos:

- API
- Frontend
- Painel Administrativo

---

# Packages

Contêm bibliotecas reutilizáveis.

Os packages representam camadas arquiteturais.

---

# Workspaces

O projeto utiliza **npm Workspaces**.

Razões:

- solução oficial do Node.js
- simplicidade
- zero dependências adicionais
- excelente integração com TypeScript
- onboarding simplificado

---

# Porque não pnpm?

Embora o pnpm ofereça vantagens de desempenho, a equipa decidiu privilegiar simplicidade operacional.

A migração futura permanece possível caso o projeto cresça significativamente.

---

# Versionamento

Todo o código é versionado em conjunto.

Não existem versões independentes entre packages.

---

# Benefícios

- desenvolvimento mais simples

- refatorações globais

- partilha de tipos

- partilha do domínio

- testes integrados

- documentação centralizada

---

# Escalabilidade

Esta estrutura suporta naturalmente:

- aplicações móveis

- workers

- marketplace

- APIs

- micro-serviços futuros

sem necessidade de reorganização física do repositório.