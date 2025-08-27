---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-10-2024 18:54:10
links:
  - "[[Lecture 08102024111650]]"
---
# Equivalenza tra NFA e grammatiche regolari
---
## Introduzione
> Data una [[Grammatiche regolari|grammatica regolare]] $G$ si può costruire un [[NFA]] $N_{G}$ equivalente.

## Dimostrazione
Fissiamo $G = (NT, T, R, S)$, allora $N_{G} = (T, Q, \delta, q_{0}, F)$ è definito come:
- $Q = NT \cup \{\epsilon\}$
- $F = \{\epsilon\}$
- $q_{0} = S$

mentre $\delta$ è definita come:
- $V \to aZ \in R \implies z \in \delta(v, a)$, ossia se è nello stato $v$ e legge $a$ passa allo stato $z$;
- $V \to a \in R \implies \epsilon \in \delta(v, a)$, ossia se è nello stato $v$ e legge $a$ passa all'unico stato finale $\epsilon$;
- $S \to \epsilon \in R \implies \epsilon \in \delta(S, \epsilon)$, ossia se è nello stato iniziale $S$, con una transizione-$\epsilon$ può andare nello stato finale $\epsilon$;

Avendo definito $N_{G}$ in questo modo, si dimostra che
$$S {\implies_{G}}^{*} w \iff (S, w) {\vdash_{N_{G}}}^{*} (\epsilon, \epsilon)$$
ossia che dal simbolo iniziale $S$ si [[Derivazione|deriva]] una stringa $w$ sse dallo stato iniziale $S$ e con la lettura di $w$ si iterano delle mosse (un cammino) che portano allo stato finale $\epsilon$ e con la stringa di lettura $\epsilon$ (vuota).

La dimostrazione è omessa.

**Qed**.

## Referenze