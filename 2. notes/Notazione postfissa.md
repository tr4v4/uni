---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 16:22:54
links:
  - "[[Lecture 27022025131944]]"
---
# Notazione postfissa
---
## Introduzione
> La **notazione postfissa** e' una notazione per esprimere [[Espressione|espressioni]] in cui _gli operatori seguono gli operandi_.

E' molto piu' semplice della [[Notazione infissa|notazione infissa]]:
- non servono regole di precedenza;
- non servono regole di associatività;
- non servono le parentesi;
- l'[[Algoritmo|algoritmo]] di valutazione e' naive, utilizza solo una [[Pila|pila]].

## Algoritmo
L'algoritmo di valutazione di un'espressione in notazione postfissa e' il seguente:
1. leggi il prossimo simbolo dell’espressione e mettilo sulla pila
2. se il simbolo letto è un operatore:
	1. applica a operandi immediatamente precedenti sulla pila
	2. memorizza il risultato in R
	3. elimina operatore ed operandi dalla pila
	4. memorizza il valore di R sulla pila
3. se la sequenza da leggere non è vuota o e' un operando torna a (1)

## Referenze