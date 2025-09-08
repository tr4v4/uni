---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 08-09-2025 16:16:09
links:
---
# Grammatiche LALR(k)
---
## Introduzione
Si parte dall'[[DFA dei prefissi viabili|automa canonico]] $LR(k)$ e si fondono insieme gli stati con lo stesso nucleo (item $LR(0)$).

Se la tabella risultante non presenta conflitti, e non esistono $w_{1}, w_{2}$ sulle colonne tali che $w_{1}$ e' prefisso di $w_{2}$ con una riga su cui le 2 celle sono entrambe riempite, allora $G$ e' $LALR(k)$.

## Referenze
- [[Grammatiche LR(k)]]
- [[Grammatiche SLR(k)]]