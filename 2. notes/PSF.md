---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 14:32:48
links:
  - "[[Lecture 11112024131700]]"
---
# PSF
---
## Introduzione
> Per **PSF** (**Point Spread Function**), nell'[[Imaging|imaging]] si intende una funzione $\mathcal{A}$ che realizza una _distorsione deterministica_ di un'immagine $x$, che _simuli l'errore dello strumento di cattura_, come ad esempio una imperfezione dell'obiettivo o del sensore.
> Viene _modellizzata come l'effetto di una [[Convoluzione|convoluzione]] $K$_. In particolare, se $x$ è l'immagine originale, e $\mathcal{P}$ la sua [[Matrice estesa|estensione]], allora la PSF $\mathcal{A}$ su $x$ è definita come
> $$\mathcal{A}(x) = [K * (x | \mathcal{P})]$$

Questa distorsione può derivare dal movimento relativo tra la sorgente luminosa e il sensore, dalla presenza di polvere o graffi sulla lente, o da altri fattori. Fatto sta che _si assume che non dipenda dalla posizione della fonte_, o in altre parole che la PSF sia **spazio invariante**: la distorsione è la stessa per ogni punto dell'immagine.

## Referenze