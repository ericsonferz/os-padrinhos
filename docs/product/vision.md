# Visão do Produto — Os Padrinhos

> Versão: 1.0
> Estado: Aprovado
> Objetivo: Definir a visão, missão e princípios orientadores do domínio.

---

# O que é o Os Padrinhos?

**Os Padrinhos** é uma plataforma digital de planeamento e gestão de casamentos, concebida para acompanhar o casal desde a primeira ideia até à conclusão de todos os eventos que fazem parte da celebração.

Mais do que um organizador de tarefas ou um marketplace de fornecedores, o sistema funciona como um assistente inteligente de planeamento, ajudando o casal a tomar decisões, estimar custos, organizar participantes, contratar serviços e acompanhar toda a execução do projeto.

O domínio foi concebido para refletir a realidade cultural e operacional dos casamentos em Moçambique, mantendo flexibilidade para acomodar diferentes tradições, estilos e formatos de celebração.

---

# Missão

Simplificar o planeamento de casamentos através de uma plataforma que transforma decisões complexas em processos organizados, previsíveis e colaborativos.

---

# Visão

Ser a plataforma de referência para o planeamento de casamentos em Moçambique e, futuramente, noutros mercados africanos, integrando planeamento, orçamento, fornecedores e execução numa única experiência.

---

# O Problema que Resolvemos

O planeamento de um casamento envolve dezenas de decisões, centenas de tarefas e múltiplos intervenientes.

Na prática, os casais recorrem frequentemente a folhas de cálculo, grupos de WhatsApp, cadernos, documentos dispersos e contactos informais de fornecedores.

Esta fragmentação provoca:

- perda de informação;
- dificuldade em controlar o orçamento;
- falta de organização;
- decisões pouco informadas;
- dificuldade em comparar fornecedores;
- pouca previsibilidade dos custos.

O Os Padrinhos procura eliminar essa fragmentação através de um único sistema integrado.

---

# Princípios Fundamentais

## 1. O casamento é um projeto

O casamento é tratado como um projeto com objetivos, orçamento, participantes, fases e resultados.

Todo o sistema organiza-se em torno do `WeddingProject`.

---

## 2. O planeamento é orientado por decisões

O centro do domínio não são os fornecedores.

Também não são os eventos.

O centro do domínio são as necessidades reais do casal.

Cada decisão de planeamento origina novas necessidades que alimentam o restante sistema.

---

## 3. As necessidades ligam todo o domínio

Uma necessidade pode originar:

- estimativas de custo;
- tarefas;
- procura de fornecedores;
- contratação de serviços;
- acompanhamento da execução.

A entidade `Need` constitui o fio condutor entre os diferentes módulos da plataforma.

---

## 4. A tecnologia adapta-se ao casamento

O sistema não obriga o casal a seguir um modelo rígido.

Cada projeto pode representar diferentes tradições, culturas e formatos de celebração.

Exemplos:

- casamento civil;
- casamento religioso;
- lobolo;
- xiguiane;
- receção;
- after party;
- brunch;
- outros eventos relevantes.

---

## 5. O domínio representa a realidade

As entidades existem porque representam conceitos reais do negócio.

Não são criadas por conveniência técnica.

Cada entidade deve possuir responsabilidades claras e significado para o utilizador.

---

## 6. A simplicidade é uma prioridade

O utilizador não deve ser exposto à complexidade interna do domínio.

O sistema deve automatizar sempre que possível:

- criação de necessidades;
- checklists;
- estimativas iniciais;
- sugestões de fornecedores;
- organização da informação.

---

# Os Pilares do Produto

O produto assenta sobre cinco pilares principais.

## Planeamento

Organização dos eventos, etapas, tarefas e necessidades.

---

## Orçamento

Estimativa, acompanhamento e controlo financeiro do projeto.

---

## Marketplace

Descoberta, comparação e contratação de fornecedores e respetivos serviços.

---

## Execução

Acompanhamento da preparação e realização dos eventos.

---

## Analytics

Transformação dos dados do projeto em informação útil para apoiar decisões futuras.

---

# O que o sistema NÃO é

O Os Padrinhos não é apenas:

- uma agenda;
- uma checklist;
- um marketplace;
- um gestor financeiro.

É uma plataforma integrada de planeamento de casamentos.

---

# Filosofia Arquitetural

O domínio é desenvolvido segundo princípios de Domain-Driven Design (DDD).

As decisões de negócio têm prioridade sobre decisões técnicas.

A arquitetura procura garantir:

- elevada coesão;
- baixo acoplamento;
- linguagem ubíqua consistente;
- evolução incremental;
- facilidade de manutenção.

---

# Critério de Evolução

Novas funcionalidades só devem ser introduzidas quando reforçarem esta visão.

Se uma funcionalidade obrigar a quebrar os princípios definidos neste documento, o domínio deve ser revisto antes da implementação.

---

# Estado

Este documento constitui a visão oficial da versão inicial do domínio do projeto Os Padrinhos.