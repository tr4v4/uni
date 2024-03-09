---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 15:31:55
links:
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza dell'implica
---
## Regole
### [[Regole di introduzione|Introduzione]]
La regola d'introduzione dell'[[Implicazione|implica]] consiste, dovendo dimostrare $F_{1} \implies F_{2}$, nel supporre $F_{1}$ e dimostrare $F_{2}$.
![[regola-introduzione-implica.png]]

_E' [[Invertibilità di una regola di inferenza|invertibile]]_, quindi si applica immediatamente durante una dimostrazione.

#### [[Teorema di correttezza|Correttezza]]
Dalla definizione di correttezza, se abbiamo $F_{1} \implies F_{2} \vdash F_{1} \implies F_{2}$, dobbiamo dimostrare
$$F_{1} \implies F_{2} \Vdash F_{1} \implies F_{2}$$
ovvio.

**Qed**.

### [[Regole di eliminazione|Eliminazione]]
La regola d'eliminazione dell'implica, anche chiamata **modus ponens**, consiste, avendo come ipotesi $F_{1} \implies F_{2}$ nel dimostrare $F_{1}$ per provare $F_{2}$.
![[regola-eliminazione-implica.png]]

_Non è invertibile, neanche se abbiamo $F_{1} \implies F_{2}$ tra le ipotesi_[^1]! Questo perché $F_{1}$ potrebbe non valere ($\bot$). Perciò l'implicazione risulta essere la principale causa di [[Backtracking|backtracking]] nelle dimostrazioni.

#### Correttezza
Avendo $F_{1} \implies F_{2}, F_{1} \vdash F_{2}$, dobbiamo dimostrare
$$F_{1} \implies F_{2}, F_{1} \Vdash F_{2}$$

Dalla [[Semantica classica#Definizione|definizione di semantica classica]] si ha, fissato un [[Mondo|mondo]] $v$, che $[[F_{1}]]^{v} = 1$ e $\max \{1 - [[F_{1}]]^{v}, [[F_{2}]]^{v}\} = \max \{0, [[F_{2}]]^{v}\} = 1$, quindi $[[F_{2}]]^{v} = 1$.

**Qed**.

## Referenze
[^1]: a differenza di quanto avviene per l'[[Regole di inferenza dell'AND|AND]] e l'[[Regole di inferenza dell'OR|OR]]