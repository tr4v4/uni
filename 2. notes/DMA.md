---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 16:01:43
links:
  - "[[Lecture 21022025091223]]"
---
# DMA
---
## Introduzione
> Il **DMA** (**Direct Memory Access**) e' un meccanismo che consente a un [[Device controller|device controller]] e alla [[RAM]] si scambiarsi dati in maniera autonoma, senza aver bisogno della mediazione del [[CPU|processore]].

## Funzionamento
Il [[Sistema operativo|sistema operativo]]:
1. attiva l'operazione di I/O specificando l'indirizzo in memoria di destinazione (input) o di provenienza (output) dei dati;
2. il controller del dispositivo prende (output) o pone (input) i dati per l’operazione di I/O direttamente dalla memoria centrale;
3. l'[[Interrupt|interrupt]] specifica solamente la conclusione dell'operazione di I/O;

Per fare cio', e' necessario un nuovo dispositivo hardware: l'**arbitro del bus**, che deve coordinare l'accesso concorrente al [[Bus|bus]] (tenendo conto del fatto che la CPU ha maggiore priorita' rispetto ai device controller!).

## Referenze
- una tecnica simile meno moderna e' il [[Cycle stealing|cycle stealing]];