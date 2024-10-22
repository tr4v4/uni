---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-10-2024 19:13:12
links:
  - "[[Lecture 08102024111650]]"
---
# Equivalenza tra DFA e grammatiche regolari
---
## Introduzione
> Dato un [[DFA]] $M$ è possibile definire una [[Grammatiche regolari|grammatica regolare]] $G_{M}$ tale che
> $$L[M] = L(G_{M})$$
> ossia che il [[Linguaggio accettato|linguaggio accettato]] dall'automa è lo stesso [[Linguaggio generato|generato]] dalla [[Grammatiche|grammatica]].

## Dimostrazione
Sia $M = (\Sigma, Q, \delta, q_{0}, F)$ il DFA, allora la grammatica regolare $G_{M} = (NT, T, S, R)$ dove:
- $NT = Q$, ossia gli stati di $M$ sono i non-terminali di $G_{M}$;
- $T = \Sigma$, ossia l'alfabeto di $M$ sono i terminali di $G_{M}$;
- $S = q_{0}$, ossia lo stato iniziale di $M$ è il simbolo iniziale di $G_{M}$;

e le produzioni $R$ sono:
- $\delta(q_{i}, a) = q_{j} \implies q_{i} \to aq_{j} \in R$
- $\delta(q_{i}, a) = q_{j} \land q_{j} \in F \implies q_{i} \to aq_{j} \in R \land q_{i} \to a \in R$
- $q_{0} \in F \implies q_{0} \to \epsilon \in R$

Si può dimostrare che
$$w \in L[M] \iff w \in L(G_{M})$$

## Riflessione
> E' possibile fare lo stesso partendo da un NFA anziché da un DFA?

La risposta è no: **per l'esistenza delle transizioni-$\epsilon$**!
Infatti, una transizione-$\epsilon$ sarebbe equivalente nella grammatica ad una produzione del tipo
$$q_{i} \to q_{j}$$
dove ovviamente $q_{i}, q_{j} \in NT$. E _questo non è consentito nelle grammatiche regolari, che richiedono un terminale prima del nonterminale_.

## Referenze