# Os Padrinhos

## Para Assistentes de IA

Antes de analisar ou gerar código para este projeto, leia obrigatoriamente:

```
docs/ai-knowledge-base.md
```

Este documento contém:

- arquitetura oficial
- decisões de domínio
- linguagem ubíqua
- regras de modelação
- princípios DDD
- estilo de código
- ordem de implementação

Os restantes documentos em `/docs` aprofundam cada tema específico e devem ser consultados quando necessário.

# Project Documentation Governance

## Architecture & Implementation Progress Reports

Todos os grandes marcos do projeto devem possuir um **Architecture & Implementation Progress Report** antes da passagem para a próxima fase.

Estes relatórios servem como:

* histórico das decisões técnicas;
* evidência de implementação;
* material de auditoria externa;
* contexto para colaboradores humanos e agentes de IA.

---

## Localização

Todos os relatórios ficam armazenados em:

```
docs/reports/
```

---

## Convenção de nomes

Formato obrigatório:

```
YYYY-MM-DD-HHMM-architecture-implementation-progress-report.md
```

Exemplo:

```
2026-07-22-1500-architecture-implementation-progress-report.md
```

---

## Estrutura obrigatória

Todos os relatórios devem conter:

1. Objetivo da Fase Concluída
2. Ficheiros Criados / Modificados
3. Decisões Técnicas e de Domínio Tomadas
4. Estado dos Testes
5. Próxima Etapa Proposta

---

## Processo de Aprovação

Uma fase só é considerada concluída quando:

* a implementação estiver documentada;
* os testes estiverem registados;
* as decisões arquiteturais estiverem justificadas;
* o relatório estiver criado.

Depois disso, o projeto pode avançar para a próxima fase.
