---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 26-09-2023 09:03:08
links:
  - "[[Lecture 25092023151613]]"
---
# Type safety
---
## Definizione
> Ogni entità dev'essere usata in accordo con il suo tipo.

Da cui:
- una variabile può essere usata solo dopo essere stata dichiarata[^1]
- solamente le operazioni definite per il tipo dichiarato per la variabile possono essere applicate ad essa
- ogni operazione applicata correttamente ritorna un valore valido

Queste regole, se non rispettate, sono segnalate dal [[Compilatore|compilatore]].

Es. di violazione: `4.3 % 2`.

## Referenze
[^1]: tranne per [[Javascript]]...