---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 03-05-2025 16:34:41
links:
  - "[[Lecture 20032025151643]]"
---
# Compattazione
---
## Introduzione
> La **compattazione** è una tecnica di [[Gestione della memoria|gestione della memoria]] che consiste nel _riordinare i processi in memoria per eliminare gli spazi vuoti e migliorare l'[[Allocazione|allocazione]] della memoria_. E' un metodo per mitigare il problema della [[Frammentazione esterna|frammentazione esterna]].

## Funzionamento
Se si ha [[Binding|binding]] a _run-time_ possiamo fare compattazone, shiftando tutti i processi per riunire le aree inutilizzate (un [[Defrag|defrag]] in [[RAM]]).

Si tratta di un'operazione onerosa: non puo' essere usata in sistemi interattivi (i [[Processo|processi]] devono essere fermi durante la compattazione).

## Referenze