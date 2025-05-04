---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 27-04-2025 17:17:38
links:
  - "[[Lecture 16042025091309]]"
---
# Direzione ammissibile
---
## Introduzione
> Data una soluzione ammissibile $\bar{x} \in \mathbb{R}^{n}$ nel [[Teoria della dualita'|primale]], un [[Vettore|vettore]] $\xi \in \mathbb{R}^{n}$ e' detto **direzione ammissibile** se esiste un $\bar{\lambda} > 0$ tale che $x(\lambda) = \bar{x} + \lambda \xi$ e' ancora ammissibile nel primale per ogni $\lambda \in [0, \bar{\lambda}]$.

## Lemma
> Il vettore $\xi$ e' una direzione ammissibile per $\bar{x}$ $\iff$ $A_{I(\bar{x})} \xi \leq 0$.

### Dimostrazione
Definiamo in modo equivalente la direzione ammissibile $\xi$, tale che per ogni $i \in \{1, \cdots, m\}$ vale
$$A_{i}x(\lambda) = A_{i}\bar{x} + \lambda A_{i} \xi \leq b_{i}$$

allora distinguiamo i due casi:
- $i \in I(\bar{x}) \implies$ $A_{i} \bar{x} = b_{i}$, quindi l'equazione e' verificata $\iff \lambda A_{i} \xi \leq 0$ e quindi $\iff A_{i} \xi \leq 0$;
- $i \notin I(\bar{x}) \implies$ $A_{i} \bar{x} < b_{i}$, quindi l'equazione e' verificata per ogni $\xi$ purche' $\lambda$ sia piccolo a sufficienza.

**Qed**.

## Referenze