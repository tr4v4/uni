---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 20:54:52
links:
  - "[[Lecture 14042025091835]]"
---
# Teorema fondamentale della programmazione lineare
---
## Preliminari
Con il [[Teorema di Motzkin|teorema di Motzkin]] si da' una definizione alternativa di poliedro: _non solo come intersezione di semispazi, ma anche come somma di un politopo e di un cono convesso_.

Le due rappresentazioni sono equivalenti, ma non hanno la stessa dimensione: se si prende il poliedro di un ipercubo in $\mathbb{R}^{n}$, allora i semispazi sono $2n$ mentre i vertici sono $2^{n}$.

Di conseguenza, _i vincoli sono un modo estremamente compatto di rappresentare i poliedri, mentre i politopi e i coni un po' meno_!

## Teorema
> Sia $P = \{x | Ax \leq b\}$ e siano $x_{1}, \cdots, x_{s}, v_{1}, \cdots, v_{t} \in \mathbb{R}^{n}$ tali che
> $$P = conv(\{x_{1}, \cdots, x_{s}\}) + cono(\{v_{1}, \cdots, v_{t}\})$$
> allora il problema $\max\{cx | Ax \leq b\}$ ha ottimo finito $\iff cv_{j} \leq 0 \ \ \ \forall j \in \{1, \cdots, t\}$, e in tal caso esiste un $k \in \{1, \cdots, s\}$ tale che $x_{k}$ e' una soluzione ottima.

### Dimostrazione
Per il teorema di Motzkin si ha che il problema $\max\{cx | Ax \leq b\}$ e' equivalente al problema sulle variabili $\lambda_{1}, \cdots, \lambda_{s}, \nu_{1}, \cdots, \nu_{t}$
$$\max c\left(\sum\limits_{i=1}^{s}\lambda_{i}x_{i} + \sum\limits_{j=1}^{t} \nu_{j}v_{j}\right) = \max  \sum\limits_{i=1}^{s} \lambda_{i} (cx_{i}) + \sum\limits_{j=1}^{t} \nu_{j}(cv_{j})$$
per cui valgono
$$\sum\limits_{i=1}^{s} \lambda_{i} = 1 \land \lambda_{i} \geq 0 \land \nu_{j} \geq 0$$

Ora, dimostriamo la doppia implicazione:
- $\implies$: se per assurdo $cv_{j} > 0$ per un qualche $j \in \{1, \cdots, t\}$, allora si potrebbe aumentare illimitatamente il valore di $\nu_{j}$ e quindi anche il valore della funzione obiettivo, il che e' assurdo perche' assumiamo che l'ottimo sia finito;
- $\impliedby$: se $cv_{j} \leq 0$ per ogni $j \in \{1, \cdots, t\}$, allora se consideriamo un $y \in P$, per il teorema di Motzkin questo punto puo' essere rappresentato come $y = \sum\limits_{i=1}^{s} \lambda_{i}x_{i} + \sum\limits_{j=1}^{t} \nu_{j}v_{j}$; usando la linearita' si avra' che $cy = \sum\limits_{i=1}^{s} \lambda_{i}(cx_{i}) + \sum\limits_{j=1}^{t} \nu_{j}(cv_{j}) \leq \sum\limits_{i=1}^{s} \lambda_{i}(cx_{i}) \leq \sum\limits_{i=1}^{s} \lambda_{i}(cx_{k}) = cx_{k}$ dove $k$ e' l'indice tale per cui $cx_{k} = \max\{cx_{i}\}$; quindi $cx_{k}$ e' una soluzione ottima finita, nonche' un vertice del poliedro $P$.

**Qed**.

## Referenze