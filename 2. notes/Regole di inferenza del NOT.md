---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 06-11-2023 18:39:20
links:
  - "[[Lecture 31102023161330]]"
---
# Regole di inferenza del NOT
---
## Regole
Il presupposto fondamentale è che
$$\neg F \equiv F \implies \bot$$
ovvero che la [[NOT|negazione]] può essere scritta come un'[[Implicazione|implicazione]] dell'_assurdo_.

### [[Regole di introduzione|Introduzione]]
Se voglio dimostrare $\neg F$, usando le [[Regole di inferenza dell'implica|regole d'inferenza dell'implica]] ci si riduce a dimostrare $\bot$ supponendo $F$, ovvero
![[introduzione-not.png]]

La regola è _[[Invertibilità di una regola di inferenza|invertibile]]_ perché lo è l'introduzione dell'implicazione, ma c'è una particolarità in più: **vogliamo dimostrare $\bot$, ovvero l'assurdo**. Vuol dire che le ipotesi devono dimostrare l'assurdo, e quindi che ogni cosa diventa, di conseguenza, dimostrabile. Vale a dire, in breve, che il **sottoalbero sovrastante la dimostrazione diventa sempre invertibile**.

Bisogna invertire il modo di ragionare: se prima determinate regole prevedevano di dover riflettere in [[Approccio bottom-up|bottom-up]] per _scegliere la strada giusta_, nel ramo del $\bot$ ciò non vale più: bisogna anzi **cercare di toccare più strade possibili per raggiungere, senza _detour_, l'assurdo**!

Questa è sia una benedizione che una maledizione:
- _benedizione_ --> ogni regola diventa invertibile
- _maledizione_ --> non si ha più una guida, una strada di riferimento da tenere in considerazione

### [[Regole di eliminazione|Eliminazione]]
Se abbiamo come ipotesi $\neg F$, ci basta ottenere $F$ per dimostrare l'assurdo (sempre in linea con le regole d'inferenza dell'$\implies$):
![[eliminazione-not.png]]

Anche questa è invertibile.

## Osservazione
Quando si dimostra l'assurdo si tendono ad accumulare ipotesi (_toccare più strade_), per questo l'**albero tende a crescere verticalmente**.

## Referenze