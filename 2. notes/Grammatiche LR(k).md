---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 08-09-2025 16:02:41
links:
---
# Grammatiche LR(k)
---
## Introduzione
Le caratteristiche principali delle grammatiche $LR(k)$ possono essere riassunte nei seguenti punti:
- _item $LR(k)$ = $[\text{item } LR(0), \beta]$ con $|\beta| \leq k$_;
- _item iniziale = $[S' \to S, \$]$_;
- _quando $[A \to \alpha . X\gamma, \beta] \in s$ (stato dell'[[DFA dei prefissi viabili|automa canonico]] $LR(k)$), allora anche $[X \to .\delta, w] \in s$ se $X \to \delta$ e' una produzione ($\in R$) e $w \in \text{First}_{k}(\gamma\beta)$_;
- _[[Tabella di parsing LR|tabella di parsing]] con colonne su $T \cup \{\$\}$ (per shift e accept), piu' tutti i $w$ tale che esiste un item $[A \to \alpha., w]$ (per le reduce)_;
- _affinche $G$ sia $LR(k)$, e' necessario che la tabella di parsing $LR(k)$, ottenuta a partire dall'automa canonico $LR(k)$_
	- _contenga al piu' un'azione per ogni cella della tabella_;
	- _non esistano $w_{1}, w_{2}$ sulle colonne tali che $w_{1}$ e' prefisso di $w_{2}$ e per almeno una riga le 2 corrispondenti entrate contengano un'azione_;

<u>Nota bene</u>: le reduce sono solo messe in corrispondenza del [[Look-ahead|look-ahead]] $w$.

## Referenze
- [[Grammatiche SLR(k)]]
- [[Grammatiche LALR(k)]]