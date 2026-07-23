# WeddingProject

## Visão Geral

`WeddingProject` é o **Aggregate Root** do domínio do Os Padrinhos.

Representa o projeto completo de organização de um casamento, independentemente da sua dimensão ou complexidade.

É a principal fronteira de consistência do domínio e o ponto de entrada para todas as alterações estruturais relacionadas com o projeto.

O WeddingProject não representa um casamento, um evento ou uma cerimónia. Representa todo o processo de planeamento vivido pelo casal.

---

# Responsabilidades

O WeddingProject é responsável por:

- representar um projeto de casamento;
- gerir o ciclo de vida do projeto;
- garantir a consistência estrutural dos seus agregados filhos;
- manter o CoupleProfile;
- manter a coleção de WeddingEvents;
- publicar eventos de domínio relacionados com alterações estruturais.

---

# Não é responsável por

WeddingProject nunca deverá:

- calcular orçamentos;
- contratar fornecedores;
- gerir pagamentos;
- criar Needs;
- gerar cronogramas;
- gerir tarefas;
- gerir participantes de WeddingStages;
- executar regras do marketplace.

Estas responsabilidades pertencem a outros Aggregates ou Domain Services.

---

# Identidade

Cada WeddingProject possui um identificador imutável.

ProjectId

Este identificador nunca muda durante todo o ciclo de vida.

---

# Estado

Estados possíveis:

- Draft
- Planning
- Confirmed
- Completed
- Cancelled
- Archived

Cada transição deverá obedecer às regras de negócio definidas pelo domínio.

---

# Estrutura

WeddingProject contém:

- ProjectId
- CoupleProfile
- ProjectStatus
- Collection<WeddingEvent>
- Metadata

---

# Invariantes

As seguintes regras nunca podem ser violadas.

## 1.

Todo WeddingProject possui exatamente um CoupleProfile.

Nunca zero.

Nunca mais do que um.

---

## 2.

Todo WeddingProject possui um estado válido.

---

## 3.

Todo WeddingEvent pertence exatamente a um WeddingProject.

---

## 4.

WeddingEvents não podem existir órfãos.

---

## 5.

Um WeddingProject arquivado não pode regressar ao estado Draft.

---

## 6.

Depois de Completed não podem existir alterações estruturais.

Exemplo:

- adicionar WeddingEvents
- remover WeddingEvents
- alterar CoupleProfile

---

# Comportamentos

O Aggregate deve expor apenas comportamentos de negócio.

Exemplos:

- create()
- rename()
- changeStatus()
- addWeddingEvent()
- removeWeddingEvent()
- archive()

Evitar métodos genéricos como:

- save()
- update()
- setStatus()
- edit()

---

# Eventos de Domínio

WeddingProject poderá publicar:

- WeddingProjectCreated
- WeddingProjectRenamed
- WeddingProjectArchived
- WeddingProjectStatusChanged
- WeddingEventAdded
- WeddingEventRemoved

---

# Relações

WeddingProject

↓

1 CoupleProfile

↓

1..N WeddingEvents

---

# Limites do Aggregate

WeddingProject conhece apenas:

- CoupleProfile
- WeddingEvent

Nunca conhece diretamente:

- WeddingStage
- Need
- Vendor
- VendorService
- ServiceBooking
- BudgetItem
- AgendaItem
- Task

Estas entidades pertencem a Aggregates próprios.

---

# Regras Arquiteturais

WeddingProject é o único Aggregate Root administrativo do domínio.

Todas as alterações estruturais do projeto devem passar por ele.

Nenhuma entidade externa poderá modificar diretamente a coleção de WeddingEvents.

---

# Extensões Futuras

O modelo suporta naturalmente futuras capacidades como:

- colaboração entre múltiplos utilizadores;
- histórico (Audit Trail);
- templates de projeto;
- clonagem de projetos;
- multi-idioma;
- múltiplos organizadores;
- integrações externas.

Estas funcionalidades não fazem parte do MVP e não devem influenciar o modelo atual.

---

# Critérios de Aceitação

Um WeddingProject está corretamente modelado quando:

✓ possui identidade própria;

✓ possui exatamente um CoupleProfile;

✓ controla a coleção de WeddingEvents;

✓ protege as suas invariantes;

✓ publica eventos de domínio;

✓ não assume responsabilidades pertencentes a outros Aggregates.