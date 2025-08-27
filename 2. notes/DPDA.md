---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 18-08-2025 18:54:39
links:
  - "[[Lecture 22102024110521]]"
---
# DPDA
---
## Introduzione
> Un [[Automa a pila|PDA]] $N = (\Sigma, Q, \Gamma, \delta, q_{0}, \bot, F)$ si dice **deterministico** (**DPDA**) $\iff$:
> - $\forall q \in Q. \forall Z \in \Gamma. \delta(q, \epsilon, Z) \neq \varnothing \implies \delta(q, a, Z) = \varnothing \ \ \ \forall a \in \Sigma$;
> - $\forall q \in Q. \forall Z \in \Gamma. \forall a \in \Sigma \cup \{\epsilon\}. |\delta(q, a, Z)| \leq 1$.
> 
> Ossia, le transizioni-$\epsilon$ sono valide solo se non ci sono altre mosse per la coppia $(q, Z)$; le mosse da uno stato per uno stesso carattere in input (compreso $\epsilon$) e nella pila sono al massimo 1.

## Referenze
- [[Linguaggio libero deterministico]]