---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 02-03-2025 15:34:53
links:
  - "[[Lecture 24022025091339]]"
---
# Vincoli di assegnamento
---
## Introduzione
> I **vincoli di assegnamento** sono vincoli solitamente usati nella [[Programmazione lineare intera|programmazione lineare intera]] per esprimere situazioni in cui e' necessario _assegnare oggetti a luoghi_.
> In particolare considerati
> - $N = \{1, \ldots, n\}$ l'insieme degli oggetti
> - $V = \{1, \ldots, m\}$ l'insieme dei luoghi
> 
> vogliamo che **ogni luogo riceva un solo oggetto e viceversa**. Si fa costruendo una matrice di variabili indicizzata su coppie $i, j$, tale che $x_{ij} \in \{0, 1\}$ (**variabile logica**) modelli il fatto che l'$i$-esimo oggetto e' assegnato al $j$-esimo luogo e, trattandosi di un vincolo di assegnamento, valga
> $$\sum\limits_{j=1}^{m} x_{ij} = 1 \ \ \ \ \ \sum\limits_{i=1}^{n} x_{ij} = 1$$
> <u>Attenzione</u>: **i vincoli di assegnamento possono essere applicati se e solo se $n = m$**[^1]!

I vincoli di assegnamento possono essere usati per imporre gli $n$ oggetti (intesi come lavori) siano **eseguiti in un certo ordine** (il luogo $j$ indica l'ordine di esecuzione del lavoro $i$).

## Esempi
### Assegnamento di costo minimo
![[assegnamento-costo-minimo.png]]

#### Variabili
Modellizziamo il problema introducendo $n \times n$ _variabili logiche_ della forma $x_{ij}$, tale che
$$x_{ij} = \begin{cases} 0 & \text{i non matchato con j} \\ 1 & \text{i matchato con j} \end{cases}$$

#### Vincoli
Come prima cosa, ovviamente, dobbiamo indicare che $x_{ij}$ sono variabili logiche. Per cui deve valere che
$$\forall i,j \ \ \ x_{ij} \in \mathbb{Z}, 0 \leq x_{ij} \leq 1$$

Poi, analizzando il problema, ci accorgiamo che sono _necessari dei vincoli di assegnamento_ su [[Insiemi ammissibili|insiemi ammissibili]]. In particolare, vogliamo associare un singolo maschio $i$ con una singola femmina $j$ (vincolo di assegnamento), ma rispettando le rispettive preferenze $F(i)$ e $M(j)$ (insiemi ammissibili). Per cui, valgono i due vincoli di assegnamento
$$\sum\limits_{j \in F(i)} x_{ij} = 1 \ \ \ \ \ \sum\limits_{i \in M(j)} x_{ij} = 1$$

#### Funzione obiettivo
Definiti vincoli e variabili, la funzione obiettivo diventa semplicemente
$$(\min) \sum\limits_{i=1}^{n} \sum\limits_{j=1}^{n} x_{ij}c_{ij}$$

## Referenze

[^1]: equivale a voler creare una [[Funzione biiettiva|biezione]] tra $N$ e $V$, che devono avere quindi la stessa [[Cardinalità|cardinalita']] (in quanto finiti lo stesso numero di elementi)
