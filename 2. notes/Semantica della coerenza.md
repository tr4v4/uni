---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 18-06-2025 17:34:05
links:
  - "[[Lecture 11042025104834]]"
---
# Semantica della coerenza
---
## Introduzione
> Nei [[Sistemi operativi|sistemi operativi]] [[Multiprogramming|multiprogrammati]], i [[Processo|processi]] accedono ai file in modo indipendente, e questo potrebbe causare _problemi di coerenza tra le modifiche fatte da piu' processi contemporaneamente su uno stesso file_: e' necessario stabilire una **semantica della coerenza**.

## Coerenza immediata
In [[Unix]], la semantica della coerenza e' immediata: **le modifiche al contenuto di un file aperto sono rese disponibili agli altri processi immediatamente**.

Ne esistono 2 versioni:
- _condivisione del puntatore alla posizione corrente nel file_ (ottenibile con `fork`);
- _condivisione con distinti puntatori alla posizioni corrente_.

Nel primo caso, il processo padre e il processo figlio condividono lo stesso _file descriptor_, per questo il puntatore all'offset corrente sul file e' condiviso; nel secondo caso invece i file descriptor sono diversi.

## Coerenza delle sessioni
In [[AFS]], un [[File system|file system]] condiviso globalmente, non e' pensabile la coerenza immediata: si usa la coerenza delle sessioni.

## Referenze