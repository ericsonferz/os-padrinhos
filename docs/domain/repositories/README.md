# Repositories

## Objetivo

Repositories representam contratos de acesso aos Aggregates.

O domínio nunca conhece:

- Prisma
- Supabase
- SQL
- Mongo
- Firebase

O domínio apenas conhece interfaces.

Exemplo

IWeddingProjectRepository

create()

update()

delete()

findById()

findAll()

## Regra

Cada Aggregate Root possui o seu Repository.

WeddingProject

↓

WeddingProjectRepository

Vendor

↓

VendorRepository

Need

↓

NeedRepository

## Benefícios

- baixo acoplamento;
- testes fáceis;
- independência da infraestrutura.