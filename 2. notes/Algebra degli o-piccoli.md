---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 16-11-2023 20:11:11
links:
  - "[[Lecture 13112023094129]]"
---
# Algebra degli o-piccoli
---
## Introduzione
Ricordiamo per [[O-piccolo|o-piccolo]] intendiamo una _[[Classe|classe]] di funzioni_ $g(x)$ che per $x \to x_{0}$ si comporta in modo da annullare il limite del rapporto tra se stesso e $f(x)$. Come conseguenza, nell'**algebra degli o-piccoli** si ha che **sopravvive sempre l'o-piccolo peggiore**, ovvero il più grande, quello che approssima peggio la funzione (in ottica degli [[Sviluppo in serie di Taylor|sviluppi di Taylor]])[^1].

In particolare questo si nota nella somma/differenza tra due o-piccoli... (si vede dopo).

## Regole
Queste regole ci mostrano il comportamento algebrico degli o-piccoli, molto _simile a quello dei monomi_:
1. $f = o(x^{n}) \implies f = o(x^{m}) \iff m \leq n$
	- conseguenza della proprietà intrinseca dell'o-piccolo di essere una funzione generica
	- ovvia perché se si ha un generico o-piccolo di $x^{n}$, quello stesso o-piccolo sarà equivalente a un o-piccolo meno preciso, di ordine più basso ($m \leq n$)
	- $f = o(x^{7}) \implies f = o(x^{6}) \lor o(x^{5}) \lor o(x^{4}) \lor ...$
1. $o(x^{n}) \pm o(x^{n}) = o(x^{n})$
	- in breve, _l'o-piccolo della somma di due funzioni è l'o-piccolo più grande tra quelli delle due funzioni_
2. $x^{m} \cdot o(x^{n}) = o(x^{n+m})$
	- $x^{4} \cdot o(x^{2}) = o(x^{6})$, infatti $x^{4} \cdot x^{3} = x^{7} = o(x^{6})$
1. $o(x^{m}) \cdot o(x^{n}) = o(x^{m+n})$
2. $(o(x^{n}))^{m} = o(x^{n \cdot m})$
3. $o(o(x^{n})) = o(x^{n})$
	- non ci dice nulla in più su $o(x^{n})$
	- infatti stiamo considerando degli o-piccoli di ordine superiore a un o-piccolo di ordine superiore a $x^{n}$, ovvero proprio a un o-piccolo di ordine superiore a $x^{n}$
1. $o(x^{n} + o(x^{m})) = o(x^{n}) \iff m \geq n$
2. $o(x^{n} + \alpha x^{n+m}) = o(x^{n})$
3. $\frac{o(x^{n})}{x^{m}}= o(x^{n-m}) \iff m \leq n$
4. $o(k \cdot x^{n}) = o(x^{n}) \iff k \neq 0$
5. $o(h(x) \cdot x^{n}) = o(x^{n}) \iff h(x) \stackrel{x \to 0}{\longrightarrow} k \neq 0$

## Referenze
[^1]: come per una _catena_, la cui _resistenza complessiva è determinata dalla resistenza dell'anello più debole_