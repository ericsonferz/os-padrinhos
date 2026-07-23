# Architecture Review Process

## Objetivo

Definir oficialmente o processo de revisão arquitetural do projeto.

---

# Quando ocorre

A revisão arquitetural ocorre:

- no final de cada Milestone;
- antes de alterações estruturais;
- antes de mudanças de arquitetura;
- antes de grandes refatorações.

---

# Itens Obrigatórios

A revisão deverá verificar:

## Domínio

- Linguagem Ubíqua
- Integridade dos Aggregates
- Invariantes
- Value Objects
- Domain Services

---

## Arquitetura

- Clean Architecture
- SOLID
- DDD
- Dependency Rules
- Repository Structure

---

## Qualidade

- Testes
- Cobertura
- Complexidade
- Naming
- Legibilidade

---

# Processo

ChatGPT produz:

- código
- documentação
- testes
- relatório

↓

Gemini executa auditoria independente

↓

Caso existam recomendações:

- avaliar
- documentar
- corrigir (quando aprovado)

↓

Merge

---

# Alterações

Mudanças arquiteturais relevantes deverão:

1. ser justificadas;
2. atualizar documentação;
3. possuir ADR correspondente.

---

# Objetivo

Garantir estabilidade arquitetural durante todo o ciclo de vida do projeto.

A arquitetura deve evoluir de forma controlada, nunca por alterações casuais.