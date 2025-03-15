---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 10:56:53
links:
  - "[[Lecture 20022025131602]]"
---
# Regole di visibilita' dei nomi
---
## Introduzione
> Le **regole di visibilita'** dei [[Nome|nomi]] si raccolgono in:
> 1. _regola di visibilità dei [[Blocco|blocchi]]_;
> 2. _regole di [[Scope|scope]]_;
> 3. _regole per il passaggio dei parametri_;
> 4. _regole di [[Binding|binding]]_ (solo per i linguaggi di ordine superiore, in cui le funzioni sono passate ad altre funzioni);
> 5. _regole specifiche del [[Linguaggio di programmazione|linguaggio]]_ (tipo inizializzazione di una variabile prima della sua dichiarazione, o funzioni chiamate prima di essere definite);

<u>Nota bene</u>: c'e' il caso speciale della [[Mutua ricorsione|mutua ricorsione]], infatti nella maggior parte dei linguaggi[^1] non e' possibile richiamare una [[Funzione informatica|funzione]] prima di averla dichiarata. La soluzione adottata e' o di _rilasciare il vincolo per funzioni in mutua ricorsione_, o di _usare definizioni incomplete_.

## Referenze

[^1]: tranne [[JS]]!
