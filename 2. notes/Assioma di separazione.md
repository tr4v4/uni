---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 12:02:25
links:
  - "[[Lecture 20092023125825]]"
---
# Assioma di separazione
---
## Definizione
$$\forall X, \exists Y, \forall Z,(Z \in Y \iff (Z \in X \land P(Z)))$$
ovvero
$$\text{dato un insieme, possiamo formare il sottoinsieme dei suoi elementi che soddisfano una proprietà}$$

Questo assioma è ciò che resta dell'_assioma di comprensione_ della [[Teoria naive degli insiemi|teoria naive]]! Una decisa restrizione ai criteri di creazione di insiemi.

Per semplicità, anche se non correttissimo, si usa ridurre l'assioma in "_zucchero sintetico_" (per semplificare i calcoli):
$$Y=\{Z \in X | P(Z)\}$$

Ora, per ricreare il [[Paradosso di Russell|paradosso di Russell]] sarebbe necessario partire da un insieme più grande per poter definire un suo sottoinsieme, come l'insieme universo $U$. Per cui uscirebbe:
$$Y = \{Z \in U | Z \notin Z\}$$
Il punto è che $Z \in U$ è sbagliato perché $U$ stesso non è un insieme, ma bensì una **classe**, perché troppo grande per rientrare nella categoria di insieme. Per questo il paradosso, con questo assioma, non può verificarsi.

## Referenze