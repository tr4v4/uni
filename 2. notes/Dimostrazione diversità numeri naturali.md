---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 12:57:14
links:
  - "[[Lecture 28092023090721]]"
---
# Dimostrazione diversità numeri naturali
---
## Introduzione
Non possiamo dimostrare in modo completo la diversità tra tutti i [[Numeri naturali|numeri naturali]], pertanto ci limiteremo a dimostrare $1 \neq 2$, usando la [[Costruzione dei numeri naturali|definizione di numero naturali]] e procedendo con le regole delle [[Dimostrazione in teoria assiomatica degli insiemi|dimostrazioni nella teoria ssiomatica degli insiemi]].

## Dimostrazione
Procediamo allora [[Dimostrazione per assurdo|per assurdo]], supponendo che invece $1 = 2$. Per l'[[Assioma di estensionalità|assioma di estensionalità]] stiamo quindi dimostrando che $\forall Z (Z \in 1 \iff Z \in 2)$. Prendendo come ipotesi $Z \in 2$ dobbiamo dimostrare $Z \in 1$, e poiché per l'[[Assioma del singoletto|assioma del singoletto]] e dell'[[Assioma dell'unione|unione]] $1 \in 2$, ne deduciamo che allora $1 \in 1$.

Sappiamo che $1 = \{\varnothing\}$, per cui sempre per l'assioma del singoletto se $1 \in \varnothing$ allora $1 = \varnothing$. Quindi dobbiamo dimostrare che $\{\varnothing\} = \varnothing$, che per l'assioma di estensionalità diventa $\forall Z (Z \in \{\varnothing\} \iff Z \in \varnothing)$. Prendendo come ipotesi $Z \in \{\varnothing\}$, dobbiamo dimostrare $Z \in \varnothing$, e poiché $\varnothing \in \{\varnothing\}$ per l'assioma del singoletto, allora dev'essere che $\varnothing \in \varnothing$, il che **è un assurdo** per l'[[Assioma dell'insieme vuoto|assioma dell'insieme vuoto]].

Per cui $1 \neq 2$.

## Referenze