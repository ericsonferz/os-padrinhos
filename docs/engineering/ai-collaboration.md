# AI Collaboration

## Objetivo

Este documento define oficialmente como as ferramentas de Inteligência Artificial participam no desenvolvimento do projeto **Os Padrinhos**.

As IAs são consideradas ferramentas de engenharia assistida e não substituem a revisão humana nem o processo de arquitetura definido pelo projeto.

---

# Filosofia

Cada IA possui um papel específico.

Evita-se que múltiplas IAs tomem decisões arquiteturais independentes sobre o mesmo problema.

A arquitetura possui uma única direção.

---

# ChatGPT

## Papel

Lead Software Architect

Principal Backend Engineer

DDD Specialist

## Responsabilidades

- Definir arquitetura
- Definir RFCs
- Produzir código de produção
- Implementar Domain-Driven Design
- Implementar Shared Kernel
- Implementar Aggregates
- Implementar Value Objects
- Implementar Domain Services
- Implementar Application Layer
- Produzir documentação técnica
- Produzir testes unitários
- Atualizar documentação
- Produzir Progress Reports

O ChatGPT é o principal responsável pela implementação do projeto.

---

# Gemini

## Papel

Independent Architecture Auditor

## Responsabilidades

- Auditar arquitetura
- Validar DDD
- Validar Clean Architecture
- Procurar dependências incorretas
- Validar SOLID
- Encontrar acoplamentos
- Rever consistência
- Rever documentação
- Validar Progress Reports

O Gemini não substitui o ChatGPT.

O Gemini audita o trabalho produzido.

---

# Cursor

## Papel

Integrated Development Environment

Responsabilidades:

- edição de código
- refatoração
- navegação
- produtividade

O Cursor não toma decisões arquiteturais.

---

# Processo Oficial

Documentação

↓

RFC

↓

Implementação (ChatGPT)

↓

Testes

↓

Progress Report

↓

Auditoria (Gemini)

↓

Correções (caso existam)

↓

Merge

---

# Alterações Arquiteturais

Nenhuma IA pode alterar a arquitetura diretamente.

Sempre que uma auditoria sugerir alterações relevantes deverá ser criada uma ADR.

A alteração apenas poderá ocorrer após aprovação.

---

# Objetivo

Separar claramente:

- implementação
- auditoria
- documentação

garantindo maior qualidade e estabilidade ao projeto.