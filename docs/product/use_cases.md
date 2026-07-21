# USE_CASES.md

# Casos de Uso Principais — Os Padrinhos

---

# UC01 — Criar Projeto de Casamento

## Ator

Casal

## Fluxo

1. Criar WeddingProject
2. Definir CoupleProfile
3. Escolher tipo de casamento
4. Criar eventos iniciais

Resultado:

```
WeddingProject criado
```

---

# UC02 — Criar Evento

Exemplo:

Criar:

```
WeddingEvent

CASAMENTO
```

ou:

```
WeddingEvent

LOBOLO
```

Sistema cria estrutura base.

---

# UC03 — Adicionar Stage

Exemplo:

Adicionar:

```
WeddingStage

Receção
```

Sistema solicita:

* local
* data
* horário

Depois pode gerar necessidades.

---

# UC04 — Gerar Planeamento Automático

Actor:

Planning Engine

Entrada:

```
WeddingStage:
Receção
```

Resultado:

```
Needs:

Catering
DJ
Decoração
Fotografia
Segurança
```

---

# UC05 — Estimar Orçamento

Sistema analisa:

* tipo de stage
* número de convidados
* localização
* dados históricos

Cria:

```
BudgetItems
```

Exemplo:

```
Buffet

Estimativa:
350.000 MT
```

---

# UC06 — Procurar Fornecedor

Entrada:

```
Need:

Fotografia
```

Sistema:

1. identifica categoria
2. procura VendorServices
3. apresenta fornecedores compatíveis

---

# UC07 — Contratar Serviço

Fluxo:

```
Need

↓

VendorService

↓

ServiceBooking
```

Atualiza:

* orçamento
* estado operacional
* histórico

---

# UC08 — Gerir Participantes

Adicionar:

```
Participant

Maria da Silva
```

ao:

```
WeddingEvent
```

Automaticamente disponível nos Stages.

Caso especial:

Criar:

```
ParticipantAssignment
```

para restringir presença.

---

# UC09 — Executar Evento

Durante o casamento:

Sistema acompanha:

* tarefas
* pagamentos
* fornecedores
* agenda

---

# UC10 — Pós-evento

Dados reais alimentam:

* analytics
* preços médios
* recomendações futuras
* inteligência do Planning Engine

---

# Princípio geral

O Os Padrinhos não começa pelo fornecedor.

Começa pela pergunta:

"Que necessidade existe neste momento do casamento?"

A partir daí:

```
Necessidade

↓

Planeamento

↓

Orçamento

↓

Fornecedor

↓

Execução
```
