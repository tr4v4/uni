---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
date: 05-05-2024 18:12:58
links:
  - "[[Lecture 24042024092014]]"
---
# Base ortonormale
---
## Introduzione
> Si definisce **base ortonormale** di uno [[Spazio vettoriale|spazio vettoriale]] $\mathbb{R}^{n}$ una [[Base|base]] costituita da $n$ _[[Vettore|vettori]] ortonormali_, ovvero tali per cui per $v_{1}, \cdots, v_{n}$ vale che
> $$<v_{i}, v_{j}> = \delta_{ij} = \begin{cases}1 & i = j \\ 0 & i \neq j\end{cases} \ \ \ \forall i, j \in \{1, \cdots, n\}$$
> ovvero che il [[Prodotto scalare|prodotto scalare]] a due a due di ogni vettore della base sia uguale al _delta di Kronecker_, ossia a 1 $\iff$ $v_{i} = v_{j} \iff i = j$; e a 0 se invece $v_{i} \neq v_{j} \iff i \neq j$.
> Nota la differenza con la [[Base ortogonale|base ortogonale]], per cui non è richiesto che $||v_{i}|| = 1$ perché i vettori della base non devono essere [[Normalizzazione|normalizzati]].

### Esempi
Si prendano $e_{1}, e_{2} \in \mathbb{R}^{2}$: questi formano una base ortonormale, non per niente quella [[Base canonica|canonica]]. Così come $e_{1}, e_{2}, e_{3} \in \mathbb{R}^{3}$.
In generale diremo che _$\{e_{1}, \cdots, e_{n}\}$ è una base ortonormale di $\mathbb{R}^{n}$_.

## Proposizioni
### Lineare indipendenza
> Siano $v_{1}, \cdots, v_{k} \in \mathbb{R}^{n}$ vettori non nulli e a due a due ortogonali, allora $v_{1}, \cdots, v_{k}$ sono [[Indipendenza lineare|linearmente indipendenti]].

Come importante corollario della proposizione si ha che, per il [[Teorema del completamento|teorema del completamento]], **il numero massimo di vettori non nulli di $\mathbb{R}^{n}$ ortogonali tra loro è $n$**.

#### Dimostrazione
Devo dimostrare l'indipendenza lineare di $v_{1}, \cdots, v_{k}$, allora uso la definizione e dimostro
$$\lambda_{1}v_{1} + \cdots + \lambda_{k}v_{k} = \underline{0} \iff \lambda_{1} = \cdots = \lambda_{k} = 0$$

Prendiamo in considerazione solo il seguente caso
$$<\underline{0}, v_{1}> = 0$$
Allora sostituisco il vettore nullo con $\lambda_{1}v_{1} + \cdots + \lambda_{k}v_{k}$ e dimostro
$$<\lambda_{1}v_{1} + \cdots + \lambda_{k}v_{k}, v_{1}> = 0 \iff \lambda_{1} = \cdots = \lambda_{k} = 0$$

Quindi, per la bilinearità del prodotto scalare posso scrivere
$$\lambda_{1}<v_{1}, v_{1}> + \cdots + \lambda_{k}<v_{k}, v_{1}> = 0$$
ed essendo i vettori ortogonali a due a due ho $<v_{i}, v_{1}> = 0 \ \ \forall i \neq 1$, perciò non rimane che
$$\lambda_{1} <v_{1}, v_{1}> = 0$$
ed essendo $v_{1}$ non nullo per ipotesi allora il risultato viene $\iff$
$$\lambda_{1} = 0$$

Ripetendo questo procedimento per i $k$ vettori si ottiene che ogni scalare $\lambda$ dev'essere uguale a 0, confermando la tesi.

**Qed**.

### Coordinate rispetto a una base
> Sia $\beta = \{v_{1}, \cdots, v_{n}\}$ una base ortonormale di $\mathbb{R}^{n}$, allora preso un vettore $v \in \mathbb{R}^{n}$ si ha che
> $$(v)_{\beta} = (<v, v_{1}>, \cdots, <v, v_{n}>)$$
> ovvero che le sue [[Coordinate rispetto a una base|coordinate rispetto alla base]] $\beta$ sono il prodotto scalare tra $v$ e ogni vettore della base.

#### Dimostrazione
Sappiamo che $v$ è [[Combinazione lineare|combinazione lineare]] di $v_{1}, \cdots, v_{n}$, ovvero
$$v = \lambda_{1}v_{1} + \cdots + \lambda_{n}v_{n}$$

Per cui, per la definizione di coordinate, dobbiamo solo dimostrare che $\lambda_{1} = <v, v_{1}>, \cdots, \lambda_{n} = <v, v_{n}>$.

Preso allora un generico $v_{i}$ dimostro $<v, v_{i}> = \lambda_{i}$:
$$<v, v_{i}> = <\lambda_{1}v_{1} + \cdots + \lambda_{n}v_{n}, v_{i}>$$
che per la bilinearità del prodotto scalare si traduce in
$$<v, v_{i}> = \lambda_{1}<v_{1}, v_{i}> + \cdots + \lambda_{i}<v_{i}, v_{i}> + \cdots + \lambda_{n}<v_{n}, v_{i}>$$

Quindi, essendo $v_{1}, \cdots, v_{n}$ ortonormali tra loro, "sopravviverà" soltanto $<v_{i}, v_{i}> = 1$, da cui
$$<v, v_{i}> = \lambda_{i}$$

**Qed**.

## Referenze