---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 15:37:06
links:
  - "[[Lecture 12112024091405]]"
---
# Variazione totale
---
## Introduzione
> La **variazione totale** è una [[Regolarizzazione|tecnica di regolarizzazione]] usata nell'[[Imaging|imaging]] per risolvere il [[Problemi inversi|problema inverso]] $Ax = y^{\delta}$. In particolare, se $x$ è l'immagine di partenza, si calcola la varianza totale $TV(x)$ come la [[Norma vettoriale|norma 1]] del [[Gradiente|gradiente]] di $x$:
> $$TV(x) = \|\nabla x\|_{1} = \sum\limits_{i=1}^{M}\sum\limits_{j=1}^{N} \sqrt{(x_{i+1,j} - x_{i,j})^{2} + (x_{i,j+1}, x_{i,j})^{2}}$$
> A tale funzione, non essendo [[Funzione differenziabile|differenziabile]] in $(0, 0)$, viene aggiunto un parametro $\beta > 0$ (nell'ordine di $10^{-3}$):
> $$TV(x) = \sum\limits_{i=1}^{M}\sum\limits_{j=1}^{N} \sqrt{(x_{i+1,j} - x_{i,j})^{2} + (x_{i,j+1}, x_{i,j})^{2} + \beta^{2}}$$
> Il problema di regolarizzazione diventa allora
> $$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2} + \lambda TV^{\beta}(x)$$
> che può essere risolto usando il [[Metodo di discesa del gradiente|metodo di discesa del gradiente]] (magari usando backtracking).

<u>Nota bene</u>: il **gradiente di un'immagine è un indice fondamentale dell'imaging**. Infatti, _ogni immagine (in scala di grigi) può essere vista come una funzione_ (discreta) _in 3 dimensioni_.

## Vantaggi
La variazione totale è una tecnica molto usata in quanto permette di ottenere immagini con _bordi ben definiti_ e _pochi dettagli_, riducendo il rumore e migliorando la qualità dell'immagine.

## Referenze