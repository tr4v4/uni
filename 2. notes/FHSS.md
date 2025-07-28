---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 11:51:07
links:
  - "[[Lecture 14042025111851]]"
  - "[[Lecture 28042025111320]]"
---
# FHSS
---
## Introduzione
> Il **Frequency Hopping Spread Spectrum (FHSS)** è una tecnica di [[Codifiche wireless|codifica wireless]] che prevede la _trasmissione di dati su frequenze diverse in modo rapido e casuale_, per ridurre le interferenze e migliorare la sicurezza.

Ogni tot. tempo mittente e destinatario scelgono di cambiare frequenza. La sequenza delle frequenze e' determinata casualmente.

Vantaggi:
- le interferenze "mirate" (narrowband) sono limitate a brevi periodi;
- implementazione semplice;
- si usa solo una piccola porzione dello spettro in ogni istante;

Svantaggi:
- non e' robusto quando [[DSSS]];
- e' facile da indovinare la sequenza di frequenze;

## Versioni
Esistono due versioni di FHSS:
- _fast hopping_ - tante frequenze per bit;
- _slow hopping_ - tanti bit per frequenza;

![[fhss.png]]

## Referenze