---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 12:49:55
links:
  - "[[Lecture 15042025152135]]"
---
# QPSK
---
## Introduzione
> La **Quadrature Phase Shift Keying (QPSK)** è una tecnica di [[Modulazione|modulazione]] digitale che rappresenta i dati _variando la fase di un segnale portante_, utilizzando _quattro fasi per rappresentare due bit alla volta_.

## Tecnica
Il suo diagramma fase-ampiezza e' il seguente:
![[qpsk-diagramma.png|250]]

Questo significa che ogni simbolo rappresenta 2 bit, e si differenzia dagli altri da uno shift di fase di 90 gradi ($\frac{\pi}{2}$ radianti), mantenendo l'ampiezza invariata.

Di seguito uno schema per capire come apparirebbe un segnale QPSK:
![[qpsk-segnale.png]]

### Errori
Chiaramente, essendoci meno differenza tra i simboli, questa **tecnica di modulazione e' piu' soggetta ad errori in caso di interferenza**!

In tal caso, infatti, il ricevitore determina il valore dei bit sulla base del quadrante in cui atterra il simbolo.
![[qpsk-errore.png]]

Ma cosa succede se il simbolo atterra nel quadrante sbagliato per via di una forte interferenza? Possiamo unire le tecniche:
1. se il canale e' rumoroso, si usa [[BPSK]], cosi' da incrementare l'area di separazione tra i simboli, e quindi ridurre gli errori;
2. non appena il canale e' pulito, si usa [[QPSK]], cosi' da aumentare la velocita' di trasmissione.

Inoltre, bisogna considerare il ruolo del labelling dei quadranti: per minimizzare gli errori, bisogna che **ogni quadrante abbia come adiacenti quadranti con [[Distanza di Hamming|distanza di Hamming]]** (differenze dei valori dei bit) **minima**! Se per esempio il simbolo `00` fosse in un quadrante adiacente a `11`, allora _un'interferenza potrebbe portare a un errore di 2 bit, invece che di 1_!

<u>Nota bene</u>: il motivo per cui e' importante che solo 1 bit sia sbagliato e non 2, risiede nei [[Rilevamento degli errori|meccanismi di rilevamento e correzione degli errori]].

## Referenze