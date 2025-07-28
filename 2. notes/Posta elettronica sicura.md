---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 13:26:13
links:
  - "[[Lecture 24022025111633]]"
  - "[[Lecture 25022025152711]]"
---
# Posta elettronica sicura
---
## Introduzione
> La **posta elettronica sicura** e' un insieme di [[Protocollo|protocolli]] adottati per garantire confidenzialita', autenticazione e integrita' alle email di [[Posta elettronica|posta elettronica]].

## Funzionamento
![[posta-elettronica-sicura.png]]

Se $A$ vuole mandare una email sicura $m$ a $B$, allora:
1. [[Firma digitale|firma digitalmente]] con la sua chiave privata l'[[Funzione hash|hash]] di $m$ --> $K_{A}^{-}(h(m))$;
2. cifra con una chiave simmetrica $K_{S}$ il tutto, e invia il risultato accoppiato a $K_{S}$ cifrato con la chiave pubblica di $B$ --> $K_{B}^{+}(K_{S})$.

Raggruppando tutto, invia la coppia
$$(K_{B}^{+}(K_{S}), K_{S}(m, K_{A}^{-}(h(m))))$$
dove:
- il primo elemento garantisce confidenzialita';
- il secondo elemento garantisce confidenzalita', autenticazione e integrita';

Questo sistema si chiama [[PGP]].

## Referenze