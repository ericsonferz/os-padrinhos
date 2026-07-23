# Architecture Progress Report
**Data:** 22 Julho 2026

---

# Objetivo da Sessão

O objetivo desta sessão foi concluir definitivamente a fase de arquitetura do domínio (DDD), consolidando todas as decisões tomadas ao longo das últimas semanas e preparando o projeto para iniciar a implementação do backend do zero.

No final desta sessão, ficou decidido que o domínio do **Os Padrinhos** está oficialmente congelado e qualquer alteração estrutural futura deverá ser tratada como uma decisão arquitetural excecional.

---

# Decisões Arquiteturais

## 1. Reinício completo da implementação

Foi tomada a decisão de abandonar completamente a implementação anterior.

O repositório antigo foi preservado em:

```text
os-padrinhos-OLD/
```

Foi criado um novo repositório limpo:

```text
C:\Users\User\Documents\DEV\ospadrinhos
```

A implementação será reconstruída do zero utilizando exclusivamente a arquitetura DDD definida na documentação.

---

## 2. Organização da documentação

A documentação foi reorganizada para refletir claramente os diferentes contextos do projeto.

Estrutura atual:

```text
docs/
├── architecture/
├── domain/
├── product/
├── vision/
├── ai-knowledge-base.md
└── README.md
```

Esta organização passa a ser a estrutura oficial do projeto.

---

## 3. AI Knowledge Base

Foi criado o documento:

```text
docs/ai-knowledge-base.md
```

Este documento reúne toda a informação essencial da arquitetura para servir de contexto a diferentes assistentes de IA (ChatGPT, Claude, Gemini, Grok, etc.).

O README passou a indicar este ficheiro como principal fonte de conhecimento do projeto.

---

## 4. Documentação de Arquitetura

Foram revistos e consolidados os documentos da pasta:

```text
docs/architecture/
```

incluindo:

- architecture.md
- api-boundaries.md
- decisions.md

Foi igualmente definido um novo conjunto de princípios para orientar qualquer futuro colaborador do projeto.

---

## 5. Domínio consolidado

Durante esta sessão foram concluídos praticamente todos os documentos do domínio.

Foram documentados:

- Aggregates
- Value Objects
- Domain Events
- Domain Services
- Domain Rules
- Ubiquitous Language
- Context Map

Foi igualmente concluída a documentação individual dos Aggregates.

---

## 6. Enums

Foi decidido centralizar todos os Enumerations do domínio num único documento.

Estrutura:

```text
docs/domain/enums/
└── enums.md
```

Os Enums passam a representar exclusivamente conceitos estáveis do negócio.

---

## 7. Specifications

Foi introduzido oficialmente o padrão Specification.

Foi criado o documento:

```text
docs/domain/specifications/specifications.md
```

As Specifications serão responsáveis por validar regras de negócio reutilizáveis.

Exemplos:

- CanBookVendorSpecification
- CanCloseWeddingProjectSpecification
- StageRequiresVenueSpecification
- VendorCanProvideNeedSpecification

---

## 8. Policies

Foi igualmente introduzido o conceito de Domain Policies.

Documento:

```text
docs/domain/policies/policies.md
```

As Policies representam estratégias de negócio, distinguindo-se das Specifications por definirem comportamento em vez de validação.

Exemplos:

- AutomaticNeedGenerationPolicy
- GuestInheritancePolicy
- BudgetRollupPolicy
- VendorRecommendationPolicy

---

## 9. Filosofia de implementação

Foi tomada uma decisão importante relativamente ao estilo do domínio.

O projeto seguirá um modelo de domínio rico mas pragmático.

As entidades:

- possuem comportamento;
- protegem invariantes;
- escondem estado interno;
- não possuem setters públicos;
- utilizam métodos de negócio.

Toda a criação de entidades será realizada através de métodos estáticos `create()`.

---

## 10. Regra das Cinco Perguntas

Antes de criar qualquer nova classe, deverão ser respondidas cinco perguntas obrigatórias.

1. Porque esta classe existe?
2. Quem é o Aggregate Owner?
3. Que invariantes protege?
4. Quem pode modificá-la?
5. Que Domain Events pode emitir?

Caso estas perguntas não possam ser respondidas, a classe não deverá existir.

---

## 11. Ordem oficial de implementação

Foi definida a ordem definitiva para desenvolvimento do backend.

```text
backend/
└── domain/
    ├── shared/
    ├── value-objects/
    ├── enums/
    ├── events/
    ├── specifications/
    ├── policies/
    ├── repositories/
    ├── services/
    └── aggregates/
```

Os Aggregates apenas serão implementados depois de toda a infraestrutura do domínio estar concluída.

---

## 12. Shared Kernel

Foi decidido que o primeiro código a implementar será o Shared Kernel.

Componentes previstos:

- AggregateRoot
- Entity
- ValueObject
- UniqueEntityID
- Result
- Guard
- DomainEvent
- DomainException

Este conjunto servirá de base para todo o domínio.

---

# Estado atual

Pode considerar-se encerrada a fase de arquitetura.

A documentação encontra-se suficientemente madura para suportar uma implementação completa.

O domínio encontra-se congelado.

As próximas sessões serão dedicadas exclusivamente à implementação do código.

---

# Próxima etapa

Iniciar o desenvolvimento do Shared Kernel.

Primeira pasta:

```text
backend/domain/shared/
```

Primeiros ficheiros:

```text
AggregateRoot.ts
Entity.ts
ValueObject.ts
UniqueEntityID.ts
Result.ts
Guard.ts
DomainEvent.ts
DomainException.ts
```

A partir deste momento toda a implementação será guiada pela documentação construída durante a fase de modelação.