---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-10-2023 10:56:04
links:
  - "[[Lecture 09102023094657]]"
  - "[[Lecture 13102023133536]]"
---
# Punto di accumulazione
---
## Introduzione
> Un punto $\bar{x} \in \mathbb{R}$ di un insieme $A \subseteq \mathbb{R}$ viene definito **punto di accumulazione** di $A$ se
> $$\forall r > 0: A \cap (I_{r}(\bar{x}) \setminus \{\bar{x}\}) \neq \varnothing$$
> ovvero, **un punto è di accumulazione di un insieme se per ogni [[Intorno|intorno]] meno il punto cade almeno un punto nell'insieme**.

Se prendiamo l'insieme $A$ e ne scegliamo un punto $\bar{x}$, per capire se è di accumulazione o meno dobbiamo chiederci se per ogni intorno di quel punto (tolto $\bar{x}$ stesso) cade almeno un punto dell'intorno in $A$. Infatti l'intersecazione tra $A$ e l'intorno di $\bar{x}$ dev'essere diverso dall'[[Assioma dell'insieme vuoto|insieme vuoto]].

Se si dimostra che _per ogni_ intorno ($\forall r > 0$) l'intorno cade sempre dentro $A$ allora $\bar{x}$ è un punto di accumulazione.
![[punto-di-accumulazione.png]]

Si definisce ora l'insieme **derivato** di $A$ ($D(A)$) l'insieme che contiene tutti i punti d'accumulazione di $A$, ovvero
$$D(A) = \{\bar{x} \in \mathbb{R} | \bar{x} \text{ punto di accumulazione di } A\}$$

## Proposizione
$$\bar{x} \text{ di accumulazione per } A \iff \exists a_{n} \subseteq A : a_{n} \neq \bar{x} \ \ \forall n \land a_{n} \rightarrow_{n \to +\infty} \bar{x}$$

Vale a dire che $\bar{x}$ è un punto di accumulazione dell'insieme $A$ _sse esiste una [[Successione numerica|successione]] $a_{n}$ cui elementi sono un sottoinsieme di $A$ diversa da $\bar{x}$ per ogni valore della successione ma che ha limite $\bar{x}$ se tende a $+\infty$_.

Infatti il punto di accumulazione si può definire come _un punto a cui ci si può avvicinare indefinitamente_ rimanendo dentro l'insieme di appartenenza ($A$).

## Referenze