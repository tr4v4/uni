---
tags:
  - category/note
  - status/ongoing
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 20:05:44
links:
  - "[[Lecture 05032025091441]]"
---
# Taglio s-t
---
## Introduzione
> Un **taglio s-t**, o **$(s,t)$-taglio** e' un [[Taglio|taglio]] di una [[Rete|rete]] (o [[Grafo|grafo]]) $(N_{s}, N_{t})$ in cui
> - $s \in N_{s}$ e
> - $t \in N_{t}$.

## Nodi di frontiera
Dato un $(s,t)$-taglio, si definiscono i seguenti sottoinsiemi di frontiera
$$A^{+}(N_{s}, N_{t}) = \{(i, j) \in A | i \in N_{s} \land j \in N_{t}\}$$
$$A^{-}(N_{s}, N_{t}) = \{(i, j) \in A | i \in N_{t} \land j \in N_{s}\}$$
In altri termini, questi **sono i sottoinsiemi dei nodi che collegano le due partizioni $N_{s}, N_{t}$**.

![[taglio-s-t.png]]

## Lemma
> Per ogni $(s,t)$-taglio $(N_{s}, N_{t})$, e per ogni [[Flusso|flusso]] ammissibile $x$ con valore $v$:
> 1. $$v = \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij}$$
> 2. $$v \leq \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} u_{ij}$$

### Dimostrazione
#### 1.
Dimostriamo quell'uguaglianza, mostrando l'[[Regole di inferenza del RAA|assurdo]] per il caso $<$ e per il caso $>$.

##### $<$
Suppongo
$$v < \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij}$$

Preso il caso banale di una rete composta solo da sorgente e destinazione, e da un arco $(t, s)$, tale che la prima sommatoria sia pari a $0$, avremo che
$$v + \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij} < 0$$

##### $>$
Suppongo
$$v > \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij}$$

Preso il caso banale di una rete composta solo da sorgente e destinazione, e da un arco $(s, t)$, tale che la seconda sommatoria sia pari a $0$, allora non posso scegliere un flusso $x$ che abbia un valore $v$ superiore alla prima sommatoria. Infatti si deve per forza avere $v = x_{st}$.

## Referenze