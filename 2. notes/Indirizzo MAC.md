---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 01-10-2024 19:46:32
links:
  - "[[Lecture 20092024132015]]"
---
# Indirizzo MAC
---
## Introduzione
Serve un modo per identificare gli host di una rete, così da indirizzare messaggi non broadcast.

Ad ogni [[Scheda di rete|scheda di rete]], allora, viene associato un indirizzo MAC: 48 bit scritti in 6 coppie di cifre esadecimali separate da due punti. Le prime 3 coppie identificano l'OUI (Organizationally Unique Identifier), ossia l'azienda produttrice; le ultime 3 sono univoche per la scheda.

Questo dovrebbe garantire che in tutto il mondo non esistano due schede di rete con lo stesso indirizzo MAC. Tuttavia i cinesi hanno violato tutto, vendendo schede di rete il cui indirizzo MAC era personalizzabile.

## Referenze