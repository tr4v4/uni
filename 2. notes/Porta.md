---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 15:53:39
links:
  - "[[Lecture 27112024132652]]"
---
# Porta
---
## Introduzione
> Una **porta**, nell'ambito delle [[Rete|reti]], è un _numero di 16 bit che identifica un'applicazione in esecuzione su un host_. Viene usata in connubio con un [[Indirizzo IP|indirizzo IP]] ([[Socket|socket]]) per _identificare univocamente un'applicazione in esecuzione su Internet_.

Il processo di smistamento dei pacchetti arrivati a un host verso le rispettive applicazioni in ascolto sulle porte viene gestito dai protocolli di [[Livello trasporto|livello trasporto]]: [[TCP]] e [[UDP]].

## Numeri
Le porte si dividono in tre categorie, a seconda del loro valore:
- **ben noti** - 0-1023, riservati per i servizi più comuni;
- **registrati** - 1024-49151, assegnati a servizi registrati;
- **dinamici** - 49152-65535, assegnati dinamicamente dal [[Sistema operativo|sistema operativo]].

## Referenze