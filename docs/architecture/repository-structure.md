# Repository Structure

## Objetivo

Este documento define a estrutura física oficial do repositório do projeto **Os Padrinhos**.

A organização foi desenhada para suportar uma arquitetura baseada em Domain-Driven Design (DDD), Clean Architecture e princípios SOLID, permitindo que o sistema evolua durante muitos anos sem necessidade de reorganizações profundas.

---

# Estrutura Geral

```text
ospadrinhos/
│
├── .github/
│   └── workflows/
│
├── apps/
│   ├── api/
│   ├── frontend/
│   └── admin/                 (futuro)
│
├── packages/
│   ├── application/
│   ├── domain/
│   ├── infrastructure/
│   └── shared/
│
├── docs/
├── scripts/
├── tests/
├── tools/
│
├── package.json
├── tsconfig.base.json
├── README.md
├── LICENSE
└── .editorconfig
```

---

# Apps

As aplicações executáveis vivem em `apps/`.

Cada aplicação possui o seu próprio ciclo de vida e depende dos packages.

Exemplos:

- API
- Frontend
- Painel Administrativo
- Workers (futuro)

---

# Packages

Todo o código reutilizável vive em `packages/`.

Cada package possui uma responsabilidade bem definida.

## domain

Contém exclusivamente regras de negócio.

É o coração do sistema.

Não depende de infraestrutura.

---

## application

Contém casos de uso.

Orquestra o domínio.

Não implementa regras de negócio.

---

## infrastructure

Implementa detalhes técnicos.

Exemplos:

- Base de dados
- Repositórios concretos
- Serviços externos
- Configuração

---

## shared

Contém apenas componentes técnicos reutilizáveis.

Nunca contém regras de negócio.

Exemplos:

- Logger
- Helpers
- Configuração
- Tipos técnicos

---

# Documentação

Toda a documentação vive em `docs/`.

O código nunca deverá substituir documentação.

A documentação é considerada a fonte oficial de conhecimento do projeto.

---

# Testes

Todos os testes vivem em `tests/`.

Nenhum teste deverá ser colocado dentro do domínio.

---

# Scripts

Scripts de automação ficam em `scripts/`.

Exemplos:

- geração de código
- migrações
- importações
- manutenção

---

# Ferramentas

Ferramentas auxiliares ficam em `tools/`.

Exemplos:

- generators
- CLI internas
- utilitários de desenvolvimento

---

# Evolução

A estrutura deverá permanecer estável ao longo do crescimento do projeto.

Novos módulos deverão ser adicionados respeitando esta organização.