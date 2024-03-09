---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 12:08:38
links:
  - "[[Lecture 20092023125825]]"
---
# Definizione di intersezione
---
## Definizione
### Intersezione binaria
Se vogliamo intersecare due insiemi, la definizione di $\cap$ è
$$A \cap B \stackrel{\text{def}}{=} \{X \in A | X \in B\}$$
Ricavabile comunque dell'[[Assioma di separazione|assioma di separazione]]: stai creando un _sottoinsieme di $A$ che rispetti la proprietà di essere contenuto in $B$_.

#### Teorema dell'intersezione binaria
Risulta allora ovvio e dimostrabile (per l'assioma di separazione) che
$$X \in A \cap B \iff X \in A \land X \in B$$

### Intersezione _n_-aria
Se invece vogliamo una definizione più generale per indicare l'insieme di intersecazione tra un numero non definito di insiemi (anche infinito), allora la definizione di $\bigcap$ è
$$\bigcap F \stackrel{\text{def}}{=} \varnothing \text{ se } F = \varnothing$$
$$\bigcap F \stackrel{\text{def}}{=} \{X \in A | \forall Y, (Y \in F \implies X \in Y)\} \text{ dove } A \in F$$
La definizione, ovviamente, non dipende dall'$A$ scelto: potrebbe essere qualunque insieme di $F$.

## Referenze