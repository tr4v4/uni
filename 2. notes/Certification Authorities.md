---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 13:02:01
links:
  - "[[Lecture 24022025111633]]"
---
# Certification Authorities
---
## Introduzione
> Una **CA** (**Certification Authority**) e' un _ente super-partes che produce coppie di [[Crittografia asimmetrica|chiavi pubbliche e private]]_, e a _chiunque ne faccia richiesta gliela spedisce associandoci un'identita' digitale_.

## Funzionamento
Se $B$ fa richiesta a una CA per ottenere un'identita' digitale, quest'ultima **manda a $B$ la sua chiave privata**, e **mantiene nel suo [[Database|database]] la chiave pubblica all'interno del certificato di $B$**. L'intero certificato digitale di $B$ (compresa la sua chiave pubblica) e' cifrato con quella privata della CA: si dice che e' [[Firma digitale|firmata digitalmente]].
![[ca-certificazione.png]]

Ora, se $A$ vuole accertarsi dell'identita' di $B$, contatta la CA di riferimento. Se non conosce la sua chiave pubblica ne contatta un'altra da cui otterra' la chiave pubblica della CA di suo interesse. Ottenuta la sua chiave pubblica, richiede alla CA la chiave pubblica di $B$. Questa restituira' ad $A$ il certificato digitale di $B$, firmato con la sua chiave privata (della CA). A questo punto $A$ potra' scoprire la chiave pubblica di $B$ decifrando il suo certificato con la chiave pubblica della CA.
![[ca-autenticazione.png]]

<u>Nota bene</u>: _questi certificati hanno una scadenza_.

## Sicurezza
Una stessa CA potrebbe essere in realta' Trudy: come facciamo ad essere sicuri che non sia cosi'? Attraverso il [[Web of trust|web of trust]]: **esistono tante CA che si certificano a vicenda**, per cui Trudy per poter impersonare una CA dovrebbe impersonarle tutte.

## Referenze