---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 11:36:01
links:
  - "[[Lecture 12032025091447]]"
---
# Grafo residuo
---
## Introduzione
> Data una [[Rete|rete]] ([[Grafo|grafo]]) $G=(N, A)$ e un [[Flusso|flusso]] ammissibile $x$, il **grafo residuo** $G_{x}$ è il _multigrafo_ $(N_{x}, A_{x})$ tale che:
> - $N_{x} = N$, ossia i nodi sono gli stessi di $N$;
> - per ogni arco $(i, j) \in A$ si costruisce in $A_{x}$:
> 	- _arco concorde_ se $x_{ij} < u_{ij}$, perché posso spingere altro flusso da $i$ a $j$;
> 	- _arco discorde_ se $x_{ij} > 0$, perché eventualmente posso anche diminuire il flusso da $i$ a $j$, con un arco di verso opposto, ossia da $j$ a $i$;

<u>Nota bene</u>: si tratta di un _multigrafo perché eventualmente si possono avere più archi da $i$ a $j$_; infatti se $0 < x_{ij} < u_{ij}$, allora devo fare sia l'arco concorde che quello discorde, e se $0 < x_{ji} < u_{ji}$ a sua volta devo fare entrambi gli archi, per cui tra $i$ e $j$ ci saranno 4 archi, due concordi e due discordi!

<u>Nota bene</u>: non mettiamo le capacità.

## Referenze