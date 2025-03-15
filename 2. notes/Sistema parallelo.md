---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 06-03-2025 10:12:44
links:
  - "[[Lecture 20022025151640]]"
---
# Sistema parallelo
---
## Introduzione
> Un **sistema parallelo** e' un _singolo elaboratore che contiene piu' unita' di elaborazione_.

Fondamentalmente si fa riferimento all'architettura dei [[Multiprocessori|multiprocessori]].

## Tassonomie
### Struttura
Un sistema parallelo puo' essere di due tipi:
- [[SIMD]] --> le [[CPU]] eseguono all'unisono lo stesso programma su dati diversi[^1];
- [[MIMD]] --> le CPU eseguono programmi differenti su dati differenti;

### Dimensione
A seconda del numero e della potenza dei processori un sistema parallelo si divide in:
- _sistemi a basso parallelismo_ --> pochi processori ma molto potenti;
- _sistemi massicciamente paralleli_ --> tanti processori non troppo potenti;

### Sistema operativo
A seconda della gestione del [[Sistema operativo|SO]], i sistemi paralleli si dividono in:
- [[SMP]] --> ogni processore esegue una copia identica del sistema operativo;
- [[ASMP]] --> ad ogni processore e' assegnato un compito specifico dal sistema operativo;

## Referenze

[^1]: come nel caso delle [[GPU]]
