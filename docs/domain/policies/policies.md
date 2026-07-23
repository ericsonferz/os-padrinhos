# Domain Policies

## Objetivo

As Domain Policies representam decisões de negócio que orientam o comportamento do sistema.

Ao contrário das Specifications, uma Policy não responde apenas "sim" ou "não".

Ela define **como o domínio deve comportar-se** perante determinadas situações.

Uma Policy pode envolver vários Aggregates, Domain Services e Specifications.

---

# Diferença entre Policy e Specification

Specification

↓

Valida regras.

Exemplo

Pode contratar este fornecedor?

↓

true / false

---

Policy

↓

Define comportamento.

Exemplo

Como escolher fornecedores para esta Need?

↓

Algoritmo / Estratégia

---

# Organização

As Policies representam decisões estáveis do negócio.

Nunca representam detalhes técnicos.

Nunca representam regras da interface.

---

# AutomaticNeedGenerationPolicy

## Objetivo

Define quando o Planning Engine gera automaticamente novas Needs.

---

## Responsabilidades

- analisar WeddingStage
- analisar templates
- gerar Needs obrigatórias
- evitar duplicações

---

## Exemplo

WeddingStage

↓

Receção

↓

Gerar automaticamente

- Catering
- Música
- Decoração
- Fotografia

---

# GuestInheritancePolicy

## Objetivo

Define como os participantes são herdados.

---

## Regra

WeddingEvent

↓

Participants

↓

WeddingStage

Caso existam ParticipantAssignments

↓

utilizar apenas os atribuídos

Caso contrário

↓

herdar todos os Participants.

---

# BudgetRollupPolicy

## Objetivo

Define como o orçamento é consolidado.

---

BudgetItem

↓

WeddingStage

↓

WeddingEvent

↓

WeddingProject

---

Nunca existem valores editados manualmente.

Todos os totais são calculados.

---

# VendorRecommendationPolicy

## Objetivo

Define como o Marketplace recomenda fornecedores.

---

Critérios possíveis

- Categoria
- Localização
- Faixa de preço
- Avaliações
- Disponibilidade
- Histórico

---

A recomendação nunca escolhe automaticamente um fornecedor.

A decisão pertence sempre ao casal.

---

# NeedPrioritizationPolicy

## Objetivo

Define prioridade automática das Needs.

---

Exemplos

Local

↓

Crítica

Fotografia

↓

Alta

Open Bar

↓

Média

Lembranças

↓

Baixa

---

# StageCompletionPolicy

## Objetivo

Define quando um WeddingStage pode ser considerado concluído.

---

Pode depender de

- Needs
- Tasks
- Bookings
- Checklist

---

A política pode variar conforme o tipo do Stage.

---

# EventCompletionPolicy

## Objetivo

Define quando um WeddingEvent está concluído.

---

Todos os WeddingStages

↓

Completed

↓

WeddingEvent Completed

---

# ProjectCompletionPolicy

## Objetivo

Define quando o WeddingProject termina.

---

Todos os Events concluídos

↓

Projeto concluído

---

# SimulationPolicy

## Objetivo

Define como o Simulation Engine produz estimativas.

---

Pode considerar

- cidade
- número de convidados
- tipo de WeddingStage
- época do ano
- histórico
- inflação

---

# MarketplaceMatchingPolicy

## Objetivo

Define como uma Need encontra VendorServices compatíveis.

Fluxo

Need

↓

VendorCategory

↓

VendorServices

↓

Vendor

---

# BookingPolicy

## Objetivo

Define regras gerais de contratação.

Exemplos

- apenas Vendors ativos
- apenas Services ativos
- impedir reservas duplicadas

---

# PaymentPolicy

## Objetivo

Define regras financeiras.

Exemplos

- sinais
- pagamentos parciais
- liquidação

---

# NotificationPolicy

## Objetivo

Define quando notificações devem ser geradas.

Exemplos

- Need criada
- Booking confirmado
- Pagamento recebido
- Task atrasada

---

# TemplateApplicationPolicy

## Objetivo

Define como Templates são aplicados.

Um Template nunca altera dados existentes.

Apenas cria novos elementos quando permitido.

---

# CulturalPlanningPolicy

## Objetivo

Representa conhecimento cultural do domínio.

Exemplos

Lobolo

↓

Needs específicas

↓

Tasks específicas

↓

Checklist específica

---

Casamento Religioso

↓

Needs diferentes

↓

Agenda diferente

↓

Checklist diferente

---

# Design Principles

Policies representam decisões do domínio.

Não pertencem à infraestrutura.

Não conhecem banco de dados.

Não conhecem API.

Não conhecem interface.

São reutilizáveis em qualquer implementação.
