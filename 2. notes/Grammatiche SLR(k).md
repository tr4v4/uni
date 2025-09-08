---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 08-09-2025 16:11:09
links:
---
# Grammatiche SLR(k)
---
## Introduzione
A partire dall'[[DFA dei prefissi viabili|automa canonico]] $LR(0)$ si riempie la tabella di parsing $SLR(k)$, che ha colonne su $T \cup \{\$\}$ e in piu' sui $w \in \text{Follow}_{k}(A)$ per $A \to \alpha.$, nel seguente modo:
- _se $[A \to \alpha.] \in s$ e $A \neq S'$, inserisci "reduce $A \to \alpha$" in $M[s, w]$ per tutti i $w \in \text{Follow}_{k}(A)$_;

Se la tabella di parsing cosi' riempita non ha conflitti, e se non esistono $w_{1}, w_{2}$ sulle colonne tali che $w_{1}$ e' prefisso di $w_{2}$ con una riga su cui le 2 celle sono entrambe riempite, allora $G$ e' $SLR(k)$.

## Referenze
- [[Grammatiche LR(k)]]
- [[Grammatiche LALR(k)]]