---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 15:26:37
links:
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza del TOP
---
## Regole
### [[Regole di introduzione|Introduzione]]
La regola d'introduzione del $\top$ rispecchia il suo essere un [[Assioma|assioma]]. Per dimostrare il vero ho finito: so per certo che è già vero.
![[regola-introduzione-top.png]]
_E' una regola [[Invertibilità di una regola di inferenza|invertibile]]_.

#### [[Teorema di correttezza|Correttezza]]
Per la definizione di correttezza si ha
$$\Vdash \top$$

vero in quanto **$\top$ è vero in ogni [[Mondo|mondo]] $v$**.

### [[Regole di eliminazione|Eliminazione]]
La regola d'eliminazione del $\top$ è **inutile**, perché usando il vero come ipotesi non si ricavano nuove informazioni per provare $F$:
![[regola-eliminazione-top.png]]

Di fatto si tratta di un _detour_, ovvero di una deviazione inutile che ti riporta a dover dimostrare la tesi di partenza $F$.

## Referenze