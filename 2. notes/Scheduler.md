---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 18:42:55
links:
  - "[[Lecture 06032025151956]]"
---
# Scheduler
---
## Introduzione
> Lo **scheduler** e' il componente piu' importante del [[Kernel|kernel]], che _gestisce l'avvicendamento dei [[Processo|processi]]_, assegnando la [[CPU]] di volta in volta a un processo secondo le politiche di [[Scheduling|scheduling]] adottate.

## Funzionamento
In particolare, quando viene invocato dal [[Sistema operativo|sistema operativo]], decide quale processo viene mandato in esecuzione. Interviene:
- a seguito di una richiesta di un'operazione di [[I-O]];
- quando un'operazione di I-O termina (scatenando un [[Interrupt|interrupt]]);

<u>Nota bene</u>: in quest'ultimo caso e' incluso quello dell'[[Interval timer|interval timer]], che si comporta come un device di I-O.

## Referenze
- [[Context switch]]