---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/analisi-I
  - topic/logica-per-informatica
date: 18-09-2023 21:27:59
links:
  - "[[Lecture 18092023093106]]"
  - "[[Lecture 28092023090721]]"
  - "[[Lecture 11102023131154]]"
---
# Prodotto cartesiano
---
## Definizione
> Il prodotto cartesiano tra due [[Insiemi numerici|insiemi]] $A \times B$ corrisponde a
> $$\{(a,b): a \in A \land b \in B\}$$
> ovvero alla combinazione in _[[Coppia ordinata|coppie ordinate]]_ di ogni elemento di $A$ per ogni elemento di $B$.

Si nota infatti che $A \times B \neq B \times A$, perché $(a, b) \neq (b, a)$.

### Teorema dell'esistenza
$$\forall A, \forall B, \exists C, \forall Z,(Z \in C \iff \exists a, \exists b, (a \in A \land b \in B \land Z = (a, b)))$$
Si chiama _prodotto_ cartesiano perché il numero di elementi al suo interno è il numero di elementi di $A$ moltiplicato al numero di elementi di $B$.

Infatti
$$\{a, b\} \times \{1, 2\} = \{\{a, 1\}, \{a, 2\}, \{b, 1\}, \{b, 2\}\}$$
($2 \times 2 = 4$).

## Regole
$$A \times \varnothing = \varnothing$$
Questo vale perché se il prodotto cartesiano è l'insieme delle coppie ordinate degli elementi dei due insiemi, essendo $\varnothing$ vuoto (per l'[[Assioma dell'insieme vuoto|assioma dell'insieme vuoto]]), non contiene alcun elemento che potrebbe far coppia con elementi di $A$.

## Pratica
Il prodotto cartesiano viene usato per rappresentare gli spazi vettoriali di determinati insiemi numerici. L'esempio più famoso è per $\mathbb{R}$:
- $\mathbb{R}$ --> 1D (_linea_)
- $\mathbb{R}^2=R \times R$ --> 2D (_piano_)
- $\mathbb{R}^3=R \times R \times R$ --> 3D (_spazio_)

## Referenze