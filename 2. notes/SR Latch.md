---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 14-10-2023 16:00:50
links:
  - "[[Lecture 12102023130419]]"
---
# SR Latch
---
## Introduzione
Un primo esempio di [[Circuiti sequenziali|circuito sequenziale]] è il **SR Latch** (_Set-Reset_), che sfrutta un **ciclo** (non ammesso nei [[Circuiti combinatori|circuiti combinatori]]) per _memorizzare un valore_.
![[SR-latch.png]]
## Composizione
Si compone di due porte [[NOR]] cui rispettivo output di uno è input dell'altro.

## Funzionamento
Casi:
- `S = 1`, `R = 0` --> `Q = 1` (viene memorizzato il valore 1)
- `S = 0`, `R = 1` --> `Q = 0` (viene memorizzato il valore 0)
- `S = 0`, `R = 0` --> `Q = valore memorizzato`
- `S = 1`, `R = 1` --> `Q = 0` (il circuito è costruito in modo tale che questa possibilità non si verifichi)

## Referenze
- [[SR Latch temporizzato]]