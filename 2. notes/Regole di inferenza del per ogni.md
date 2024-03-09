---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 27-11-2023 18:33:15
links:
  - "[[Lecture 16112023092027]]"
---
# Regole di inferenza del per ogni
---
## Introduzione
### [[Regole di introduzione|Introduzione]]
Per dimostrare $\forall x . P$ mi basta _dimostrare $P$ per un generico $x$ fissato_. Attenzione però allo [[Shadowing|shadowing]]: utilizzo una [[Sostituzione|sostituzione]] e sfrutto la [[Alpha-convertibilità|alpha-convertibilità]] per ottenere lo stesso [[Diagramma di legame|diagramma di legame]].
![[introduzione-per-ogni.png]]

_E' una regola [[Invertibilità di una regola di inferenza|invertibile]]_.

### [[Regole di eliminazione|Eliminazione]]
Sapendo $\forall x . P$ _posso scegliere un termine $t$ per cui vale $P$_.
![[eliminazione-per-ogni.png]]

_Non è invertibile_, la generalizzazione può infatti mettere in un vicolo cieco a meno che non si abbia $\forall x . P$.

<u>Attenzione</u>: questa regola **di solito si utilizza per ultima**, insieme all'[[Regole di inferenza dell'esiste#Regole di introduzione Introduzione|introduzione dell'esiste]].

## Referenze