---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 16:18:14
links:
  - "[[Lecture 26092024120454]]"
  - "[[Lecture 17102024120438]]"
---
# Albero di derivazione
---
## Introduzione
Partendo da una [[Grammatiche|grammatica]], l'idea è che ad ogni [[Derivazione|derivazione]] posso associare un **albero di derivazione**, ossia una _struttura che riassuma tutte le possibili derivazioni che producano la stessa stringa_ (dette _equivalenti_).

Consideriamo per esempio la grammatica
$$S \to a | b | c | S+S | S*S$$

La derivazione _[[Derivazione canonica sinistra|leftmost]]_
$$S \implies S*S \implies S+S*S \implies a+S*S \implies a+b*S \implies a+b*c$$
è associabile all'albero di derivazione
![[albero-di-derivazione-1.png]]

La derivazione _[[Derivazione canonica destra|rightmost]]_
$$S \implies S*S \implies S*c \implies S+S*c \implies S+b*c \implies a+b*c$$
genera lo stesso albero di derivazione!

<u>Osservazione</u>: esiste una corrispondenza biunivoca tra derivazioni _leftmost_ e _rightmost_ e alberi di derivazione. Di fatto:
1. _dato un albero di derivazione esiste una sola derivazione leftmost/rightmost che lo genera_;
2. _data una derivazione leftmost/rightmost esiste un unico albero di derivazione associato_.

### Importanza
L'albero di derivazione **fornisce informazioni semantiche sulla derivazione**. In particolare, _informazioni sull'associazione operandi-operatori, e quindi sull'ordine di esecuzione delle operazioni_.

Di solito, infatti, da un albero di derivazione si ricava l'[[Albero sintattico|albero sintattico]].

## Definizione formale
> Data una [[Grammatiche libere|grammatica libera]] $G=(NT, T, S, R)$, un **albero di derivazione** (o di **parsing**) è un [[Albero|albero]] ordinato in cui:
> - _ogni nodo è etichettato con un simbolo $\in NT \cup \{\epsilon\} \cup T$_;
> - _la radice è etichettata con $S$_;
> - _ogni nodo interno è etichettato con un simbolo $\in NT$_;
> - _se il nodo $n$ ha etichetta $A \in NT$ e i suoi figli sono nell'ordine $m_{1}, \cdots, m_{k}$ con etichetta $x_{1}, \cdots, x_{k} \in NT \cup T$, allora $(A \to x_{1}, \cdots, x_{k}) \in R$, ovvero è una produzione_;
> - _se il nodo $n$ ha etichetta $\epsilon$, allora $n$ è una foglia, è figlio unico, e detto $A$ suo padre, $(A \to \epsilon) \in R$, ovvero è una produzione_;
> - _se inoltre ogni nodo foglia è etichetta su $T \cup \{\epsilon\}$, allora l'albero corrisponde a una derivazione completa_.

### Teorema
> Una stringa $w \in T^{*}$ appartiene al [[Linguaggio generato|linguaggio generato]] da $L(G)$ $\iff$ ammette un albero di derivazione completo (le cui foglie, lette da sinistra a destra, diano la stringa $w$).

## Referenze
- [[Albero sintattico]]
- [[Grammatica ambigua]]