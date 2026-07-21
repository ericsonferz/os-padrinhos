# DECISIONS.md

# Decisões Arquiteturais — Os Padrinhos

## Objetivo

Este documento regista as decisões fundamentais do domínio do Os Padrinhos.

Estas decisões devem ser consideradas a fonte de verdade antes de alterações estruturais no código.

---

# 1. Aggregate Root Principal

## Decisão

`WeddingProject` é o Aggregate Root principal do sistema.

## Responsabilidade

Representa o projeto completo de planeamento do casamento.

Inclui:

* casal
* eventos
* participantes globais
* estado do projeto
* visão consolidada financeira e operacional

Exemplo:

```
WeddingProject
João & Maria
2026
```

---

# 2. Separação entre Projeto, Evento e Stage

## Decisão

O domínio utiliza três níveis:

```
WeddingProject
    |
    WeddingEvent
        |
        WeddingStage
```

---

## WeddingProject

Representa o projeto completo.

Exemplo:

```
Casamento João + Maria
```

---

## WeddingEvent

Representa acontecimentos macro dentro do projeto.

Exemplos:

* Lobolo
* Casamento
* Xiguiane
* After Party

Cada evento possui:

* participantes principais
* orçamento agregado
* checklist
* stages

---

## WeddingStage

Representa uma unidade operacional com impacto real.

Exemplos:

* Civil
* Religioso
* Receção
* Copo de Água

Um Stage possui:

* local
* horário
* fornecedores
* necessidades
* orçamento
* tarefas

---

# 3. Regra de Peso do Domínio

Nem tudo no casamento é uma entidade.

## WeddingStage

Existe quando possui:

* regras próprias
* orçamento próprio
* fornecedores próprios
* local próprio
* impacto comercial

Exemplo:

```
Receção
DJ
Buffet
Decoração
Espaço
```

---

## AgendaItem

Existe quando é apenas um ponto cronológico.

Exemplo:

```
16:00 Entrada dos noivos
16:30 Corte do bolo
17:00 Primeira dança
```

Não possui:

* orçamento
* fornecedor
* convidados próprios

---

# 4. Participantes

## Decisão

Participantes pertencem ao WeddingEvent.

Não pertencem diretamente ao Stage.

Estrutura:

```
WeddingEvent
    |
    Participants
```

Por defeito:

```
Stage
    herda participantes do Event
```

---

## Exceções

Quando necessário:

```
ParticipantAssignments
```

Exemplo:

Civil:

* pais
* irmãos
* padrinhos

Receção:

* todos convidados

---

# 5. Need como unidade central

## Decisão

O sistema é orientado por necessidades, não por fornecedores.

Fluxo:

```
Need
 |
VendorCategory
 |
VendorService
 |
Vendor
 |
ServiceBooking
```

Exemplo:

Necessidade:

```
Precisamos de fotografia
```

Não:

```
Queremos contratar fotógrafo X
```

---

# 6. Vendor e VendorService

Fornecedor e serviço são conceitos separados.

Exemplo:

```
Vendor

Studio XPTO

    |
    Services

    Fotografia
    Drone
    Álbum
    Streaming
```

---

# 7. Orçamento

O orçamento nasce das necessidades.

Fluxo:

```
Need
 |
BudgetItem
 |
Stage Budget
 |
Event Budget
 |
Project Budget
```

O total é sempre uma agregação.

---

# 8. Planning Engine

O Planning Engine é um Domain Service.

Responsabilidade:

Transformar conhecimento cultural e operacional em:

* Needs
* Tasks
* BudgetItems preliminares

Exemplo:

Criar:

```
WeddingStage = Receção
```

gera:

```
Need:
- Catering
- Música
- Decoração
- Fotografia
- Segurança
```

---

# 9. Regra para implementação

Antes de criar novas entidades perguntar:

"Esta coisa possui comportamento próprio e impacto no negócio?"

Se não:

provavelmente é:

* atributo
* value object
* agenda item

e não uma entidade.
