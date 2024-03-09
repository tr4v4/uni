---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 17:24:15
links:
  - "[[Lecture 28092023090721]]"
---
# Relazione
---
## Definizione
> Una **relazione** tra un insieme $A$ e un insieme $B$ è un sottoinsieme del loro [[Prodotto cartesiano|prodotto cartesiano]], definito come
> $$R \subseteq A \times B$$
> Gli elementi del sottoinsieme devono rispettare la legge della relazione, per cui si scrive
> $$aRb \iff (a, b) \in R$$

### Esempio
La relazione $\leq$ è definita come
$$\leq = \{(0, 0), (0, 1), (0, 2), (1, 1), (1, 2), (2, 2), ...\}$$
e quindi
$$0 \leq 2$$
in realtà una _notazione_ per scrivere
$$(0, 2) \in \, \leq$$

## Teorema delle relazioni da/verso insiemi vuoti
$$R \subseteq A \times \varnothing \lor R \subseteq \varnothing \times A \implies R = \varnothing$$

Questo perché non posso formare [[Coppia ordinata|coppie ordinate]] prendendo uno dei due elementi dall'insieme vuoto (per l'[[Assioma dell'insieme vuoto|assioma dell'insieme vuoto]]).

## Proprietà
- [[Riflessività di una relazione]]
- [[Simmetria di una relazione]]
- [[Transitività di una relazione]]
- [[Antisimmetricità di una relazione]]
- [[Relazione di ordine stretto]]
- [[Relazione di ordine (lasco)]]
- [[Relazione di equivalenza]]

## Referenze