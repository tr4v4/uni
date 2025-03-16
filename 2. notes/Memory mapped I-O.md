---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 16:12:27
links:
  - "[[Lecture 21022025091223]]"
---
# Memory mapped I-O
---
## Introduzione
> Questa tecnica prevede che i dati gestiti dal [[I-O|dispositivo I-O]] siano direttamente mappati su un insieme di indirizzi in [[Memorie|memoria]] accessibili tramite il [[Bus|bus]].

Sono dispositivi che definiscono quindi in [[RAM]] un intervallo di indirizzi per poter dialogare, e ogni operazione di _scrittura_ e _lettura_ causa il trasferimento dei dati da o verso il dispositivo.

L'esempio piu' importante e' il **display**: in passato questo veniva gestito mappando in una specifica area di memoria tutti i valori dei pixel in modo contiguo, memorizzando per ognuno di essi i 3 valori del colore ([[RGB]]).

## Referenze