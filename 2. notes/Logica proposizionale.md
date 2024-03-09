---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 06-11-2023 18:57:43
links:
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 02112023091408]]"
---
# Logica proposizionale
---
## Introduzione
> La **logica proposizionale** è un formalismo logico in cui _ogni connotazione può denotare un valore di verità_. Parliamo a tutti gli effetti di una [[Sintassi|sintassi]], utilizzata solitamente in [[Logica classica|logica classica]].

### Esempio
In logica proposizionale, per quanto definita, la frase
> "Il gatto"

non assume alcun significato logico, per cui non rientra nella _sintassi_ prevista per essa.
Può valere invece
> "Il gatto è rosso"

perché essa può assumere un valore di verità: **vero o falso**.

## Sintassi
$$F ::= \bot | \top | A | B | ... | \neg F | F \land F | F \lor F | F \implies F$$
dove:
- $F$ è una _formula_
- $\bot$ è il _falso_
- $\top$ è il _vero_
- $A, B, ...$ sono le _variabili_
- $\neg F$ è una formula _[[NOT|negata]]_
- $F \land F$ è una _[[AND|congiunzione]]_ tra formule
- $F \lor F$ è una _[[OR|disgiunzione]]_ tra formule
- $F \implies F$ è una _[[Implicazione|implicazione]]_ tra formule

Questa è la forma in cui si presenta la sintassi della logica proposizionale, per cui vale che _la formula $F$ ha solo una delle possibili forme indicate_.

Si noti come, per come è costruita la sintassi, la logica proposizionale costituisca un esempio di [[Ricorsione|ricorsione]]: la formula $F$ tra una congiunzione $\land$, per esempio, potrebbe a sua volta essere un'altra congiunzione, e così anche per le due formule di questa.

## Rappresentazione
> Per rappresentare le funzioni semantiche vengono usati gli [[Albero di sintassi astratta|alberi di sintassi astratta]].

Per esempio:
$$\neg A \land (B \lor (C \implies D))$$
viene codificata in un albero.

## Tipologie
- [[Logica classica]]
- [[Logica intuizionista]]

## Referenze
- [[Proprietà dei connettivi e quantificatori]]