---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 10:52:11
links:
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza del BOTTOM
---
## Regole
### [[Regole di introduzione|Introduzione]]
Non esiste alcune regola d'introduzione del $\bot$: _non si può dimostrare il falso_.

### [[Regole di eliminazione|Eliminazione]]
Usando l'[[Armonia delle regole di inferenza|armonia]] deriviamo che _si dimostra $F$ se si dimostra un assurdo_. Questo vale perché dal falso segue qualunque cose.
![[regola-eliminazione-bottom.png]]

_Non è mai [[Invertibilità di una regola di inferenza|invertibile]]_, perché non esistono regole d'introduzione del $\bot$.

#### [[Teorema di correttezza|Correttezza]]
Per la definizione di correttezza si ha
$$\bot \Vdash F$$

che significa infatti che le _ipotesi sono inconsistenti_, perciò si può dimostrare qualunque cosa: **non c'è nessun [[Mondo|mondo]] in cui vale $\bot$**!

## Referenze