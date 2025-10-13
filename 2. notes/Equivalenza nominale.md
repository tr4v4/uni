---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 24-09-2025 23:45:56
links:
  - "[[Lecture 16042025110927]]"
---
# Equivalenza nominale
---
## Introduzione
> Nei [[Sistema di tipi|sistemi di tipi]] che considerano una nozione **nominale** di equivalenza (**NTE**), _ogni nuova definizione di tipo introduce un nuovo nome diverso da quelli esistenti_. Di conseguenza, se $name(T) = n$ e' una funzione che dato un tipo $T$ ne' ritorna il nome associato $n$, allora
> $$T_{1} \text{ NTE } T_{2} \iff name(T_{1}) = name(T_{2})$$
> ovvero i _due tipi sono nominalmente equivalente sse hanno lo stesso nome_.

Quindi, se definiamo `Dollaro=int` e `Euro=int` (per esempio con `typedef`), allora _`Dollaro` ed `Euro` sono tipi distinti_ in un sistema di tipi con equivalenza nominale, _nonostante in realta' il tipo sia lo stesso_ (`int`).

## Vantaggi
Ci sono tanti vantaggi del tipo nominale rispetto a quello [[Equivalenza strutturale|strutturale]]:
- stampa, marshalling, coercizione;
- denotazione dei [[Tipo ricorsivo|tipi ricorsivi]];
- sottotipaggio;

Questo e' il motivo per cui e' il _sistema di equivalenza di tipi piu' usato_.

## Referenze