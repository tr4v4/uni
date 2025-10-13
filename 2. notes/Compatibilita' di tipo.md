---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 15:13:37
links:
  - "[[Lecture 16042025110927]]"
---
# Compatibilita' di tipo
---
## Introduzione
> Per **compatibilita' di tipo** intendiamo una _forma indebolita di [[Equivalenza di tipo|equivalenza di tipo]], in cui manca nella [[Relazione di equivalenza|relazione di equivalenza]] la [[Simmetria di una relazione|simmetria]]_, creando un _preordine_.

Molti programmi corretti rispettano la compatibilita' di tipo ma non l'equivalenza.

## Definizione
Due [[Tipi di dato|tipi]] $S$ e $T$ si dicono compatibili se vale una delle seguenti cose:
- i valori di $S$ sono un sottoinsieme dei valori di $T$;
- i valori di $S$ sono un sottoinsieme di valori canonicamente corrispondenti di $T$, come da `int` a `float`;
- i valori di $S$ sono un sottoinsieme di valori arbitrari corrispondenti di $T$, facciamo una conversione noi, come da `float` a `int`;
- le operazioni sui valori di $T$ sono possibili anche sui valori di $S$;

## Conversione
Tale definizione di compatibilita' tra tipi rende _necessaria la creazione di un sistema di conversione tra tipi_, per poter colmare le differenze tra tipi non equivalenti.
I principali meccanismi di conversione sono:
- [[Coercizione di tipo|coercizione]];
- [[Casting di tipo|casting]].

## Referenze