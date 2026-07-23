# Domain Services

## Objetivo

Domain Services concentram regras que não pertencem naturalmente a uma única Entity.

Nunca guardam estado.

Nunca representam dados.

Representam comportamento.

## Exemplos

PlanningEngine

Responsável por:

- gerar Needs automáticas;
- gerar Tasks;
- gerar Budget inicial;
- aplicar templates culturais.

BudgetCalculator

Responsável por:

- calcular orçamento;
- atualizar totais;
- aplicar regras financeiras.

NeedRecommendationService

Responsável por:

- sugerir serviços;
- recomendar categorias;
- gerar estimativas.

VendorMatchingService

Responsável por:

- encontrar fornecedores compatíveis;
- ordenar resultados;
- aplicar filtros.

## Regra principal

Se uma lógica utiliza várias entidades diferentes,
provavelmente pertence a um Domain Service.