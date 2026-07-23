# VendorCategory

## Objetivo

Representa uma categoria de serviços disponíveis no marketplace.

Não representa empresas.

Não representa serviços.

Representa apenas a classificação utilizada para organizar o ecossistema de fornecedores.

---

# Exemplos

- Fotografia
- Vídeo
- Música
- Catering
- Decoração
- Espaços
- Flores
- Transporte
- Convites
- Vestuário
- Beleza
- Segurança

---

# Responsabilidades

- organizar Vendors
- facilitar pesquisas
- apoiar o Planning Engine
- permitir recomendações

---

# Não é responsável por

- preços
- contratos
- serviços específicos
- disponibilidade

---

# Atributos

- id
- name
- slug
- description
- icon
- color
- active

---

# Relacionamentos

VendorCategory

└── Vendors

      └── VendorServices

Need

↓

VendorCategory

↓

VendorServices

---

# Regras

Uma categoria pode possuir vários Vendors.

Um Vendor pertence a uma categoria principal.

Uma Need aponta para uma VendorCategory antes de procurar VendorServices.

---

# Exemplo

Fotografia

├── Studio Alpha
├── Studio Vision
├── Perfect Moments
└── Dream Weddings
