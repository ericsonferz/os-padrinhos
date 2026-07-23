# Architecture

Esta pasta contém toda a documentação técnica da arquitetura do **Os Padrinhos**.

O objetivo é preservar as decisões arquiteturais, garantir consistência entre implementações e facilitar a entrada de novos colaboradores no projeto.

## Documentos

| Documento | Objetivo |
|-----------|----------|
| architecture.md | Visão geral da arquitetura do sistema |
| decisions.md | Registo oficial das decisões arquiteturais (ADR) |
| api-boundaries.md | Limites entre módulos e bounded contexts |
| coding-principles.md | Princípios de desenvolvimento e modelação |
| development-workflow.md | Fluxo oficial de desenvolvimento |
| folder-structure.md | Organização física do projeto |
| naming-conventions.md | Convenções de nomenclatura |
| testing-strategy.md | Estratégia de testes |

## Princípios Fundamentais

- Domain-Driven Design (DDD)
- Clean Architecture
- SOLID
- Rich Domain Model (Pragmático)
- Simplicidade acima de engenharia excessiva

## Regra Principal

Sempre que existir divergência entre o código e estes documentos, considera-se que a documentação representa a arquitetura pretendida. O código deve ser atualizado para refletir as decisões aqui registadas, ou a documentação deve ser formalmente revista antes de alterar a arquitetura.