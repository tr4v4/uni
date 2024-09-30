---
tags:
  - category/note
  - status/pending
  - topic/reti-di-calcolatori
date: 27-09-2024 16:57:01
links:
  - "[[Lecture 18092024131539]]"
---
# Prestazione delle reti
---
## Introduzione
Le prestazioni di una [[Rete|rete]] si riassumono in 2 fattori principali:
- _capacità di trasmissione_
- _ritardo del collegamento_ (o _latenza_)

### Capacità di trasmissione
Questa indica il _numero massimo di bit/byte trasmessi o ricevuti in 1 secondo_.

Es.: _10 Mbyte/sec_ (o MB/s).

### Ritardo del collegamento
Questo indica il tempo richiesto ai dati per transitare da mittente a destinatario. La latenza è determinata da:
- _distanza fisica_
- _protocolli usati per la trasmissione dei dati_

Anche se spesso si fa più caso alla capacità, la latenza è importantissima: dipende dall'utilizzo della rete, ma in generale **una grande capacità non è indice di velocità**, così come **una bassa latenza non è indice di velocità**.

Es.: un videogioco online deve trasmettere pochi dati (bassa capacità) ma richiede una bassa latenza affinché funzioni bene (e non si presenti il _lag_).

### Altri indici
A volte questi indici di prestazione possono non essere sufficienti a descrivere la qualità della rete. Ci sono fenomeni come il [[Jitter|jitter]] che complicano la questione.

## Referenze