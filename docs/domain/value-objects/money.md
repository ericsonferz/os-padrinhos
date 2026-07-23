# Money

## Objetivo

Representa um valor monetário.

Money é um Value Object.

Não pode existir apenas como um número (`number`).

---

# Responsabilidades

- representar um valor financeiro
- guardar moeda
- permitir operações matemáticas
- impedir operações inválidas

---

# Atributos

- amount
- currency

---

# Exemplos

50000 MZN

250 USD

125 EUR

---

# Operações

add()

subtract()

multiply()

divide()

compare()

equals()

---

# Regras

Money é imutável.

Uma operação gera sempre um novo Money.

Nunca altera a instância atual.

---

# Exemplos

Money(1000 MZN)

+

Money(500 MZN)

↓

Money(1500 MZN)
