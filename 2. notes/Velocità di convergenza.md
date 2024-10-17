---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 04-10-2024 12:56:28
links:
  - "[[Lecture 26092024092021]]"
---
# Velocità di convergenza
---
## Introduzione
> Un [[Algoritmo iterativo|algoritmo iterativo]] ha una **velocità di convergenza** $p$ se
> $$|E_{k+1}| \leq C | E_{k}|^{p}$$
> ossia se l'_errore assoluto_ all'iterazione $k+1$ è minore o uguale a una costante $C$ per l'errore assoluto all'iterazione $k$ elevato a una costante $p$.
> In particolare si ha che:
> - $p = 1 \implies$ _convergenza lineare_
> - $1 < p < 2 \implies$ _convergenza superlineare_
> - $p = 2 \implies$ _convergenza quadratica_

### Esempi
Degli [[Algoritmi per il calcolo delle radici di una funzione|algoritmi per il calcolo delle radici di una funzione]] abbiamo visto l'[[Algoritmo di bisezione|algoritmo di bisezione]] e due algoritmi iterativi: il [[Algoritmo dell'iterazione di punto fisso|metodo del punto fisso]] e l'[[Algoritmo di Newton|algoritmo di Newton]].

Per tutti questi vale la formula:
$$|E_{k+1}| \leq C | E_{k}|^{p}$$

In particolare:
- _algoritmo di bisezione_: $C = \frac{1}{2}$ è una **costante algoritmica**, perché ad ogni iterazione si dimezza l'errore precedente;
- _algoritmo del punto fisso_: $C$ è la **costante di contrazione**, e dipende da $g(x)$, tendenzialmente $< \frac{1}{2}$ (e quindi più veloce dell'algoritmo di bisezione);
- _algoritmo di Newton_: $C$ è la **costante minima di contrazione**;

Come risultato, si ha che:
- _algoritmo di bisezione ha una convergenza lineare_;
- _algoritmo del punto fisso ha una convergenza lineare_;
- _algoritmo di Newton ha una convergenza quadratica_;

L'idea, di fatto, è che **anche se l'algoritmo del punto fisso è tendenzialmente più veloce dell'algoritmo di bisezione perché ha una costante $C$ più bassa**, **l'algoritmo di Newton è matematicamente il più veloce perché non solo ha una $C$ bassa, ma ha $p = 2$**.

## Referenze