---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 08-10-2025 18:56:44
links:
  - "[[Lecture 02102025131619]]"
---
# Random forest
---
## Introduzione
Le **random forest** sono insiemi di [[Albero di decisione|alberi di decisione]], guidati dalla tecnica ad _ensemble_: _se la maggioranza degli alberi dice $y$, allora e' $y$_.

La tecnica e' giustificata dal seguente risultato statistico: _un gran numero di modelli sufficientemente scorrelati che operano come un comitato forniscono risultati migliori dei singoli componenti_.

## Differenziazione
Il problema e' che il risultato che giustifica la tecnica ad _ensemble_, richiede tra le ipotesi la **scorrelazione statistica degli alberi**. Per ottenerla ci sono varie tecniche:
- [[Bagging|bagging]] - allenare i modelli su sottoinsiemi random (bags) dei dati di input;
- [[Feature randomness|feature randomness]] - costruire gli alberi a partire da sottoinsiemi random delle features;

## Referenze