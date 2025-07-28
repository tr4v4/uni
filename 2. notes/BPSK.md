---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 12:44:26
links:
  - "[[Lecture 15042025152135]]"
---
# BPSK
---
## Introduzione
> La **Binary Phase Shift Keying (BPSK)** è la tecnica di [[Modulazione|modulazione]] digitale su cui si basa la [[PSK]]. Ossia rappresenta i dati _variando la fase di un segnale portante_, utilizzando due fasi per rappresentare i bit 0 e 1.

### Rappresentazione di un segnale
Per poter comprendere come funziona la BSPK e le sue successive variazioni, e' importante introdurre un nuovo modo per rappresentare un segnale:
![[diagramma-ampiezza-fase.png|500]]
dove:
- $M$ e' l'ampiezza;
- $\varphi$ e' la fase;

## Tecnica
Nel dettaglio, quindi, BSPK avra' un diagramma di fase-ampiezza del tipo:
![[bpsk-diagramma.png|250]]

In altre parole, l'ampiezza e' invariata, e l'unica differenza tra 0 e 1 e' uno spostamento di fase di 180 gradi ($\pi$ radianti).

BPSK e' semplice, robusto, usato per le comunicazioni satellitari. Tuttavia sfrutta poco spettro: _pochi bit per unita' di spettro_.

## Referenze