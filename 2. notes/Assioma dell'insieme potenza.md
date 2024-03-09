---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 13:49:51
links:
  - "[[Lecture 28092023090721]]"
---
# Assioma dell'insieme potenza
---
## Introduzione
> Esiste un insieme che è formato da tutti i sottoinsiemi di un altro insieme.

$$\forall X, \exists Y, \forall Z, (Z \in Y \iff Z \subseteq X)$$
Si indica questo insieme $Y$ come $2^{X}$ o $P(X)$, talvolta detto _insieme delle parti_.

Si chiama così perché il numero possibile di sottoinsiemi di un altro insieme è uguale a 2 elevato al numero di elementi dell'insieme. Infatti prendendo per esempio
$$X = \{1, 2\}$$
allora
$$2^{X} = \{\varnothing, \{1\}, \{2\}, \{1, 2\}\}$$
($2^{2} = 4$)

## Conseguenze
Con l'unione di questo assioma con quello dell'[[Assioma dell'infinito|infinito]] è possibile ottenere insiemi più grandi! Vale a dire insiemi che superano l'ordine dell'infinito [[Numerabilità|numerabile]].

E' importante anche sottolineare che **l'insieme delle parti non produce una classe**, garantendoci che il risultato rimanga un insieme.

## Referenze