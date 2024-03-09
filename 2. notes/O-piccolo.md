---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/algoritmi-e-strutture-dati
date: 12-11-2023 18:20:10
links:
  - "[[Lecture 10112023134301]]"
  - "[[Lecture 13112023094129]]"
  - "[[Lecture 21022024111657]]"
---
# O-piccolo
---
## Introduzione
> Una [[Funzione matematica|funzione]] $g(x)$ si dice essere **o-piccolo** di $f(x)$ per $x \to x_{0}$ se, date le ipotesi
> 1. $f(x) \neq 0$ per $x \neq x_{0}$
> 2. $g(x) \stackrel{x \to x_{0}}{\longrightarrow} 0$
> 
> si ha che
> $$\lim_{x \to x_{0}} \frac{g(x)}{f(x)} = 0$$
> ovvero, **$g(x)$ è un o-piccolo di $f(x)$ se per $x \to x_{0}$ tende a $0$ più velocemente di $f(x)$, o in altre parole se $g(x)$ è un [[Infinitesimi|infinitesimo]] di ordine superiore a $f(x)$**.
> In tal caso si scrive
> $$g(x) = o(f(x))$$
> per cui $g(x)$ è una **generica funzione**[^1] che per $x \to x_{0}$ va a 0 più velocemente di $f(x)$.

### Osservazioni
La notazione
$$g(x) = o(1)$$
sta a indicare che $g(x)$ è una funzione che per $x \to x_{0}$ tende a 0: infatti _la funzione $f(x) = 1$ non tenderà mai a 0 più velocemente di qualunque altra funzione_.

## Utilizzi
Sappiamo che gli _o-piccoli_ si utilizzano per calcolare gli [[Sviluppo in serie di Taylor|sviluppi di Taylor]], e nel particolare questo significa che grazie alle loro proprietà _si è in grado di ricreare una qualunque funzione approssimandola con dei polinomi_. Quest'approssimazione prevede un errore da pagare, rappresentato proprio dagli o-piccoli.

> Trovare, di una funzione, l'_o-piccolo migliore_, significa trovare l'o-piccolo che **mantiene più informazione possibile sulla funzione di partenza**. Quello, in parole povere, più vicino alla _"soglia" d'ordine_, che se superata non fa più convergere a 0 il limite.

Se l'errore, e quindi l'o-piccolo, è molto grande (es. $o(\sqrt{x})$), perdiamo la precisione della funzione originaria! Per questo _più l'ordine dell'o-piccolo è alto meglio stiamo approssimando la funzione, perché stiamo considerando un errore infinitesimale_.

### Informatica
Nello studio degli [[Algoritmo|algoritmi]] gli $o$-piccoli fanno parte della [[Notazione asintotica|notazione asintotica]], e sono una forma più restrittiva degli [[O-grande|O-grandi]].
> Data una [[Funzione di costo|funzione di costo]] $g(n)$ definiamo l'[[insieme|insieme]] delle [[Funzione matematica|funzioni]] che sono _dominate asintoticamente_ da $g(n)$ come
> $$o(g(n)) = \{f(n) | \forall c > 0, n_{0} \geq 0 : \forall n \geq n_{0}, f(n) < cg(n)\}$$
> dove $o(g(n))$ è l'**o-piccolo** di $g(n)$.

Vale che
$$f = o(g) \implies f = O(g)$$
ma _non necessariamente il contrario_.

## Regole
- [[Algebra degli o-piccoli]]

## Referenze
[^1]: si dice essere una _[[Classe|classe]] di funzioni_