# CoupleProfile

## Objetivo

Representa o casal responsável pelo WeddingProject.

Não representa convidados.

Não representa participantes.

Representa apenas os proprietários do projeto.

---

# Responsabilidades

- armazenar informação do casal
- preferências gerais
- contactos
- identidade do casamento

---

# Não é responsável por

- lista de convidados
- orçamento
- fornecedores
- necessidades
- tarefas

---

# Atributos

- id
- bride
- groom
- preferredLanguage
- contacts
- timezone
- weddingVision
- notes

---

# Regras

Existe apenas um CoupleProfile por WeddingProject.

Nunca existe sozinho.

---

# Relacionamentos

WeddingProject
└── CoupleProfile
