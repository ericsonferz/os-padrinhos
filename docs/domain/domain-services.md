# Os Padrinhos — Domain Services

## Objetivo

Domain Services representam lógica que não pertence naturalmente a uma entidade específica.

---

# 1. PlanningEngine

## Responsabilidade

Gerar automaticamente estrutura inicial de planeamento.

Entrada:

- WeddingEvent
- WeddingStage
- cultura
- localização
- convidados

Saída:

- Needs
- Tasks
- Budget estimado

---

Exemplo:

Entrada:

WeddingStage:

Receção

300 convidados


Saída:

Needs:

- Catering
- DJ
- Decoração
- Fotografia
- Segurança

---

# 2. SimulationEngine

## Responsabilidade

Estimar custos.

Base:

- categoria
- localização
- número de convidados
- mercado

Saída:

Intervalos de preço.

Exemplo:

Fotografia:

15.000 - 35.000 MT

---

# 3. RecommendationEngine

## Responsabilidade

Recomendar fornecedores.

Critérios:

- categoria
- orçamento
- localização
- disponibilidade
- avaliação

---

# 4. BudgetCalculationService

## Responsabilidade

Consolidar valores.

Fluxo:

Stage Budget

↓

Event Budget

↓

Project Budget

---

# 5. VendorMatchingService

## Responsabilidade

Encontrar serviços adequados para uma Need.

Fluxo:

Need

↓

Category

↓

VendorService

↓

Vendor