# Engineering Principles

## Objetivo

Este documento define os princípios de engenharia que orientam todas as decisões técnicas do projeto Os Padrinhos.

São princípios permanentes e devem prevalecer sobre preferências individuais, frameworks ou tendências tecnológicas.

---

# Princípio 1 — O Domínio é a Fonte da Verdade

Todo o sistema existe para servir o domínio.

A arquitetura, infraestrutura, API e interface do utilizador são mecanismos para expor e executar regras de negócio.

Nenhuma decisão técnica poderá comprometer a integridade do domínio.

---

# Princípio 2 — Clareza antes de Tecnologia

Sempre privilegiamos soluções simples, explícitas e fáceis de compreender.

Antes de introduzir uma nova tecnologia perguntamos:

- Resolve um problema real?
- Reduz complexidade?
- Justifica o custo de manutenção?

Caso contrário, a solução mais simples deverá ser escolhida.

---

# Princípio 3 — O Código Explica o Negócio

O código deve ser escrito utilizando a Linguagem Ubíqua.

Nomes técnicos não devem substituir conceitos de negócio.

Exemplo:

✔ WeddingProject

✔ VendorCategory

✔ BudgetItem

✖ DataModel

✖ GenericEntity

---

# Princípio 4 — Dependências Apontam para o Domínio

O domínio nunca conhece:

- Frameworks
- Base de dados
- APIs
- HTTP
- ORM
- Logger
- Configuração

As dependências apontam sempre para dentro.

---

# Princípio 5 — Simplicidade

Não implementamos abstrações antes de serem necessárias.

Não antecipamos problemas hipotéticos.

Não escrevemos código para requisitos inexistentes.

---

# Princípio 6 — Testabilidade

Todo o código deverá ser facilmente testável.

Uma classe que não possa ser testada normalmente possui responsabilidades em excesso.

---

# Princípio 7 — Documentação Antes da Implementação

Antes de desenvolver um componente devem existir:

- documentação
- RFC (quando aplicável)
- definição das regras de negócio

O código implementa decisões documentadas.

Nunca o contrário.

---

# Princípio 8 — Evolução Contínua

A arquitetura poderá evoluir.

No entanto:

- nenhuma alteração estrutural é feita sem revisão;
- alterações relevantes devem ser registadas através de ADR.

---

# Princípio 9 — Qualidade Antes da Velocidade

Entregar rapidamente nunca deverá comprometer:

- legibilidade
- manutenção
- testes
- consistência

---

# Princípio 10 — Código para os Próximos Dez Anos

Sempre que possível, o código deverá ser escrito pensando na manutenção a longo prazo.

A solução mais inteligente nem sempre é a melhor.

A solução mais clara normalmente é.