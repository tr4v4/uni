---
tags:
  - category/note
  - status/ongoing
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 20:05:44
links:
  - "[[Lecture 05032025091441]]"
  - "[[Lecture 12032025091447]]"
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

In questo caso avremo:
- $A^{+} = \{(s, 1), (2, 3), (2, 4)\}$
- $A^{-} = \{(1, 2)\}$

## Lemma
> Per ogni $(s,t)$-taglio $(N_{s}, N_{t})$, e per ogni [[Flusso|flusso]] ammissibile $x$ con valore $v$:
> 1. $$v = \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij}$$
> 2. $$v \leq \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} u_{ij}$$

### Dimostrazione
#### 1.
Dimostriamo quell'uguaglianza, mostrando l'[[Regole di inferenza del RAA|assurdo]] per il caso $<$ e per il caso $>$.

Notiamo che per definizione
$$v = \sum\limits_{(s, j) \in A} x_{sj} - \sum\limits_{(i, s) \in A} x_{is}$$

Ma questo si può uguagliare a una generalizzazione della sommatoria degli archi entranti meno gli uscenti per ogni nodo in $N_{s}$:
$$\sum\limits_{(s, j) \in A} x_{sj} - \sum\limits_{(i, s) \in A} x_{is} = \sum\limits_{k \in N_{s}} \left(\sum\limits_{(j, k) \in A} x_{jk} - \sum\limits_{(k, i) \in A} x_{ki}\right)$$

Di quest'ultima sommatoria, in realtà, in tutti i nodi intermedi (ossia $\neq s$), la differenza di flusso entrante e uscente sarà 0. Alcuni di questi archi saranno di confine, ossia in $A^{+}$ o in $A^{-}$, ...

### Conseguenze
Le due quantità appena calcolate si chiamano rispettivamente:
- **flusso del taglio**, indicata con $x(N_{s}, N_{t}) = \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i,j) \in A^{-}(N_{s}, N_{t})} x_{ij}$;
- **capacità del taglio**, indicata con $u(N_{s}, N_{t}) = \sum\limits_{(i,j) \in A^{+}(N_{s}, N_{t})} u_{ij}$.

Di conseguenza, il lemma si riassume in:
$$v = x(N_{s}, N_{t}) \leq u(N_{s}, N_{t})$$

In altre parole, quindi, il lemma ci dice che _il valore di un flusso ammissibile è sempre minore o uguale alla capacità di qualunque $(s, t)$-taglio_. Ma soprattutto che, **dato un taglio, se trovo un flusso che ha valore esattamente uguale alla sua capacità** ($v = u(N_{s}, N_{t})$), **allora ho trovato il flusso massimo**. Infatti, se non fosse il massimo, allora vorrebbe dire che dato un altro taglio potrei ottenere un flusso ammissibile con valore maggiore, ma questo sarebbe un assurdo: per il lemma vorrebbe dire che $v$ supera la capacità del primo taglio.

## Referenze
- [[Teorema max-flow min-cut]]