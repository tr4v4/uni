---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
  - topic/sistemi-operativi
date: 24-11-2023 16:52:55
links:
  - "[[Lecture 20112023130829]]"
  - "[[Lecture 26022025111603]]"
  - "[[Lecture 20032025151643]]"
---
# Frammentazione interna
---
## Introduzione
> La **frammentazione interna** è una [[Frammentazione|frammentazione]] della [[RAM]], causata dalla [[Gestione della memoria|gestione della memoria]] e in particolare dai meccanismi di [[Allocazione|allocazione]].

Se un programma necessita di una _quantità di memoria che non è un multiplo della dimensione delle pagine_, una di queste verrà usata solo in parte, _lasciando "sprecata" una certa porzione di memoria_.

Formalmente, se lo spazio richiesto e' `X`, e gli si assegna un blocco di dimensione `Y > X`, allora si spreca `Y - X` spazio.

<u>Nota bene</u>: questo fenomeno si verifica al livello del [[Sistema operativo|sistema operativo]] ma anche a livello di [[Linguaggio di programmazione|linguaggio di programmazione]].

## Referenze