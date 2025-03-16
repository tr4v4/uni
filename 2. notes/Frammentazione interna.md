---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
date: 24-11-2023 16:52:55
links:
  - "[[Lecture 20112023130829]]"
  - "[[Lecture 26022025111603]]"
---
# Frammentazione interna
---
## Introduzione
> La **frammentazione interna** è una [[Frammentazione|frammentazione]] della [[RAM]] che si verifica come conseguenza della [[Paginazione|paginazione]].

Se un programma necessita di una _quantità di memoria che non è un multiplo della dimensione delle pagine_, una di queste verrà usata solo in parte, _lasciando "sprecata" una certa porzione di memoria_.

Formalmente, se lo spazio richiesto e' `X`, e gli si assegna un blocco di dimensione `Y > X`, allora si spreca `Y - X` spazio.

## Referenze