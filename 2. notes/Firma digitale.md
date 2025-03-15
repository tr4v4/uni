---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 13:14:02
links:
  - "[[Lecture 24022025111633]]"
---
# Firma digitale
---
## Introduzione
> L'idea della **firma digitale**, basata sul meccanismo "inverso" di cifratura dell'[[RSA]], consiste nell'inviare un messaggio $m$ accoppiato alla sua "firma", ovvero alla sua cifratura con la propria chiave privata $K^{-}$:
> $$(m, K^{-}(m))$$

## Funzionamento
Inviando la coppia $(m, K^{-}(m))$, cifrata magari con la chiave pubblica del destinatario per garantire confidenzialità, il destinatario puo' verificare l'[[Autenticazione|autenticita']] del mittente: decifra con la sua chiave pubblica, e vede se il risultato e' esattamente $m$.

## Integrita'
Di norma, **questo meccanismo garantirebbe anche l'integrita'**! Il problema e' la velocita' di cifratura: se $m$ e' troppo lungo, l'RSA potrebbe impiegare troppo tempo. Per questo, di solito si firma non $m$, ma un suo [[Message digest|digest]]: si fa l'[[Funzione hash|hash]] di $m$, che sara' piu' piccolo di $m$, e si cifra quello con la propria chiave privata.
Si invia quindi
$$(m, K^{-}(h(m))$$

## Referenze