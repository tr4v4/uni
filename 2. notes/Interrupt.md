---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 05-11-2023 22:50:47
links:
  - "[[Lecture 02112023130607]]"
---
# Interrupt
---
## Definizione
> Simili alle [[Trap|trap]], gli **interrupt** interrompono il programma in esecuzione e trasferiscono il controllo momentaneamente a un **gestore di interrupt** ([[ISR]], _Interrupt Service Routine_).

### Differenza con trap
La differenza fondamentale tra _interrupt_ e _trap_ sta nel fatto che queste ultime sono **sincrone**, e quindi viene scatenata ogni volta allo stesso modo da un programma che "triggera" gli eventi scatenanti; mentre gli interrupt sono **asincroni**, in quanto scatenati da altri dispositivi che sono indipendenti dal programma in esecuzione, come gli [[I-O]].

## Vantaggi
L'utilizzo degli interrupt permette di evitare il fenomeno del _busy waiting_, ovvero della continua esecuzione di istruzioni volte a verificare l'accadimento di un certo evento[^1]: _è il dispositivo stesso che, scatenato un certo evento, interrompe il programma in esecuzione e prende il controllo_.

## Tipologie
Non tutti gli interrupt possono interrompere, senza un minimo di criterio, i processi in esecuzione sulla CPU. Per questo si dividono principalmente in:
- **interrupt mascherabili** --> per cui il [[Sistema operativo|sistema operativo]] sceglie, a seconda della loro _priorità_, se interrompere o meno il processo in esecuzione
- **interrupt non-mascherabili** --> per cui a prescindere dal processo in esecuzione il sistema operativo passa il controllo all'interrupt

In generale, però, si definisce una _gerarchia di interrupt_ che stabilisce quali interrupt si possono interrompere a seconda di una _scala di priorità_:
> Un interrupt _più importante_ può interrompere il gestore di un interrupt _meno importante_.

![[gerarchie-interrupt.png]]

## Referenze
[^1]: anche detto [[Polling|polling]]