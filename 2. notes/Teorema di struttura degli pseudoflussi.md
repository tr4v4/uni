---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 20-04-2025 13:39:40
links:
  - "[[Lecture 20032025131726]]"
---
# Teorema di struttura degli pseudoflussi
---
## Introduzione
> Siano $x$ e $y$ due _pseudoflussi_ qualunque, allora esistono $k \leq n + m$ cammini aumentanti $P_{1}, \cdots, P_{k}$ per $x$, di cui al piu' $m$ cicli, tali che
> - $z_{1} = x$;
> - $z_{i+1} = z_{i} \oplus \theta_{i}P_{i} \ \ \ 1 \leq i \leq k, \ \ \ 0 \leq \theta_{i} \leq \theta(P_{i}, z_{i})$;
> - $z_{k+1} = y$.
> 
> Inoltre, tutti i $P_{i}$ hanno come estremi dei nodi in cui lo sbilanciamento di $x$ e' diverso da quello di $y$.

L'idea e' che sia sempre possibile passare da uno pseudoflusso a un altro, iterando fino a $n+m$ cammini aumentanti.

## Referenze