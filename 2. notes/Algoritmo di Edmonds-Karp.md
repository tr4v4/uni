---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 18:10:42
links:
  - "[[Lecture 19032025092241]]"
---
# Algoritmo di Edmonds-Karp
---
## Introduzione
> L'**algoritmo di Edmonds-Karp** (o **EK**) è una versione dell'[[Algoritmo di Ford-Fulkerson|algoritmo di Ford-Fulkerson]] che utilizza la visita [[BFS]] sul [[Grafo residuo|grafo residuo]] $G_{x}$ per trovare i [[Cammino aumentante|cammini aumentanti]].

Con questa piccola modifica, si ottiene che **i cammini aumentanti trovati saranno sempre di lunghezza minima**, il che _rende la [[Complessità computazionale|complessità]] dell'algoritmo polinomiale_!

## Proprietà
Per dimostrare la polinomialità, è necessario fare alcune osservazioni.

### Diminuzione distanza
Consideriamo $\delta_{x}(i, j)$ la distanza tra $i$ e $j$ nel grafo residuo $G_{x}$.

> Se durante l'esecuzione di EK il flusso $y$ è ottenuto da $x$ tramite un'operazione di aumento del flusso in un cammino aumentante, allora
> $$\forall i \in N \ \ \ \ \ \delta_{x}(s,i) \leq \delta_{y}(s, i)$$

### Complessità
> Il numero di iterazioni di EK è $O(NA)$, per cui la sua complessità è
> $$O(NA^{2})$$

#### Dimostrazione
Bisogna introdurre la nozione di **arco critico**: si tratta di quell'arco del cammino aumentante che ha come "capacità" ($u_{ij} - x_{ij}$ nel caso di archi concordi, $x_{ji}$ nel caso di archi discordi) proprio $\theta(P, x)$: è l'_arco che costituisce il bottleneck_, il minimo aumento nell'iterazione dell'algoritmo. Risulta chiaro come ne esista sempre uno in ogni cammino aumentante, ma se a una certa iterazione lo è l'arco $(i, j)$, non lo sarà all'iterazione successiva, infatti:
- se l'arco è concorde, allora gli verrà sommato $\theta$ che lo distanzia dalla sua capacità --> l'arco concorde non ci sarà più nel grafo residuo successivo;
- se l'arco è discorde, allora gli verrà sottratto $\theta$ che lo distanzia dallo 0 --> l'arco discorde non ci sarà più nel grafo residuo successivo.

Il punto è, può tornare ad essere critico? Certo che sì, ma quante volte al massimo?
Supponiamo che l'arco $(i, j)$ del cammino aumentante $P$ sia diventato critico per la prima volta, allora visto che usiamo EK vale $\delta_{x}(s, j) = \delta_{x}(s, i) + 1$. All'iterazione successiva tale arco non potrà essere critico. Ora, l'unico modo affinché torni ad esserlo è fare in modo che il flusso da $i$ a $j$ diminuisca: questo avviene se in un flusso successivo $y$ si ha $\delta_{y}(s, i) = \delta_{y}(s, j) + 1$. Dal teorema precedente, però, sappiamo che $\delta_{x}(s, i) \leq \delta_{y}(s, i)$, per cui vale
$$\delta_{y}(s, i) = \delta_{y}(s, j) + 1 \geq \delta_{x}(s, j) + 1 = \delta_{x}(s, i) + 2$$

In altre parole, se $(i, j)$ torna ad essere critico, la sua distanza da $s$ dovrà essere aumentata di almeno $2$, o più in generale non può diminuire. Di conseguenza, visto che la distanza non può essere superiore a $|N|$, il numero di volte in cui $(i, j)$ può diventare critico è lineare in $|N|$.

Ora, di coppie di archi $(i, j)$ che possono diventare critici fino a $|N|$ volte ce ne sono al massimo $|A|$, di conseguenza il numero di iterazioni di EK è proprio $O(NA)$. Considerando che ad ogni iterazione si deve fare una BFS, con costo $O(A)$, la complessità dell'algoritmo è
$$O(NA^{2})$$

**Qed**.

## Referenze