---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2025 13:59:06
links:
  - "[[Lecture 30042025110449]]"
---
# Tipi copia
---
## Introduzione
> I **tipi copia** sono introdotti in Rust per _forzare la copia dei valori piuttosto che lo [[Borrow-checking#Move|spostamento della proprieta' di ownership]] nell'assegnamento_.

A volte, infatti, sebbene la semantica del movimento di proprieta' sia efficiente, ci sono casi in cui e' piu' semplice [[Passaggio per valore|passare i valori per valore]] (e quindi per copia).

Questo accade automaticamente in Rust con i _numeri_ (interi, float), i _caratteri_, i _booleani_, le _tuple e gli array di dimensioni fisse_.

## Referenze