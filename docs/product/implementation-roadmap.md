# IMPLEMENTATION_ROADMAP.md

# Plano de Implementação — Os Padrinhos

## Objetivo

Construir o sistema em ordem correta.

---

# Fase 1 — Fundação do Domínio

Criar:

```text
WeddingProject

WeddingEvent

WeddingStage

Participant
```

Objetivo:

Ter o núcleo do planeamento.

---

# Fase 2 — Planeamento Inteligente

Criar:

```text
Need

PlanningEngine

Task
```

Objetivo:

Transformar tipos de casamento em necessidades.

---

Exemplo:

Entrada:

```text
Casamento tradicional
```

Resultado:

```text
Needs:

Buffet

Decoração

Fotografia

Música
```

---

# Fase 3 — Orçamento

Criar:

```text
BudgetItem

BudgetCalculator
```

Objetivo:

Transformar necessidades em previsão financeira.

---

# Fase 4 — Marketplace

Criar:

```text
VendorCategory

Vendor

VendorService

ServiceBooking
```

Objetivo:

Conectar necessidades a fornecedores.

---

# Fase 5 — Execução

Criar:

```text
Tasks

Agenda

Payments
```

Objetivo:

Acompanhar preparação real.

---

# Fase 6 — Inteligência

Criar:

```text
Analytics

Recommendation Engine

Market Insights
```

---

# Ordem recomendada no Cursor

Executar nesta sequência:

1.

```text
/domain/entities
```

2.

```text
/domain/value-objects
```

3.

```text
/domain/services
```

4.

```text
/application/use-cases
```

5.

```text
/infrastructure
```

6.

```text
/api
```

---

# Regra de ouro

Não criar:

* pagamentos
* contratos
* notificações
* marketplace completo

antes do domínio base funcionar.

Primeiro:

```text
Planeamento

↓

Necessidade

↓

Orçamento

↓

Fornecedor

↓

Execução
```

Essa é a espinha dorsal do produto.
