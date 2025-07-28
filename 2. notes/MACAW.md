---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 18:04:46
links:
  - "[[Lecture 06052025152121]]"
---
# MACAW
---
## Introduzione
E' come il [[MACA]] ma introduce:
- **ACK**;
- meccanismo del **binary exponential backoff**.

Andando a inserire gli ACK, la sequenza di messaggi scambiati diventa: `RTS`, `CTS`, `DATA`, `ACK`. Ma cosi' facendo significa che **il trasmettitore deve diventare anche un ricevente per l'ACK**! Anche lui, quindi, deve avere il canale libero per poterlo ricevere: serve di nuovo il carrier-sense. E in generale, quindi, **non si puo' sfruttare il canale per trasmettere in parallelo al trasmettitore**.

## Referenze