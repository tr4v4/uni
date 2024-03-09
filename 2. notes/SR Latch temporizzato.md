---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 14-10-2023 16:15:08
links:
  - "[[Lecture 12102023130419]]"
  - "[[Lecture 16102023125805]]"
---
# SR Latch temporizzato
---
## Introduzione
Come modifica al [[SR Latch]], per _evitare che questo cambi il proprio stato in particolari momenti_ o che cambi per errore (_interferenze_), si mettono in [[AND]] i due bit d'ingresso con il segnale del [[Clock|clock]], così da consentire al latch di modificarsi solo quando il segnale è a 1.
![[SR-latch-temporizzato.png]]

Insieme al [[D Latch]], l'SR Latch fa parte dei circuiti a [[Commutazione a livello|commutazione a livello]].

## Referenze