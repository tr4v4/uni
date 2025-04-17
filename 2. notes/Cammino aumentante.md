---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 11:48:21
links:
  - "[[Lecture 12032025091447]]"
---
# Cammino aumentante
---
## Introduzione
> Un **cammino aumentante** $P$ in una [[Rete|rete]] ([[Grafo|grafo]]) $G$ rispetto al [[Flusso|flusso]] $x$ è un _[[Cammino|cammino]] semplice orientato da $s$ a $t$ nel [[Grafo residuo|grafo residuo]] $G_{x}$_.

## Notazioni
Chiamiamo
- $P^{+}$ l'insieme degli archi concordi attraversati dal cammino aumentante $P$;
- $P^{-}$ l'insieme degli archi discordi attraversati dal cammino aumentante $P$.

### Capacità residua
Dato un cammino aumentante $P$ possiamo determinare la **capacità residua** $\theta$ nel seguente modo:
$$\theta(P, x) = \min\{\min\{u_{ij} - x_{ij} | (i, j) \in P^{+}\}, \min\{x_{ij} | (j, i) \in P^{-}\}\}$$

Questa funziona in questo modo:
- si prende la minima capacità residua sugli archi concordi --> indica di _quanto è possibile aumentare l'intero flusso_, affinché venga _rispettato il vincolo di capacità degli archi_;
- si prende il minimo flusso sugli archi discordi --> indica di _quanto è possibile diminuire l'intero flusso_, affinché venga _rispettato il vincolo di non negatività del flusso_;

Si osserva come **la capacità residua non sarà mai nulla**: se viene trovato un cammino aumentante, _per forza si passa per archi concordi o discordi_.

### Operatore
Si definisce ora l'operatore di aumento basato sulla capacità residua calcolata $\theta$:
$$(x(P, \theta))_{ij} = \begin{cases} x_{ij} + \theta & (i, j) \in P^{+} \\ x_{ij} - \theta & (j, i) \in P^{-} \\ x_{ij} & \text{altrimenti} \end{cases}$$

Quindi, fondamentalmente, per ogni arco $(i, j)$ di $G$, si aggiorna il suo flusso $x_{ij}$ sulla base del cammino $P$ e della capacità residua $\theta$:
- se l'arco è un arco concorde del cammino aumentante, allora il suo flusso viene aggiornato sommandoci $\theta$ --> _si aumenta il flusso trasportabile su ogni arco che lo concede_;
- se l'arco è un arco discorde del cammino aumentante, allora viene aggiornato sottraendoci $\theta$ --> _si diminuisce il flusso trasportabile per reindirizzarlo dove c'è più capacità_;
- se l'arco non fa parte del cammino aumentante, allora non viene aggiornato.

Quindi la diminuzione è importante: **diminuire il flusso in certi archi significa, per la legge di conservazione del flusso, reindirizzarlo in altri**!

## Referenze