---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 23-10-2024 23:39:10
links:
  - "[[Lecture 17102024091631]]"
  - "[[Lecture 07032025091554]]"
---
# Deadlock
---
## Introduzione
> Il **deadlock** (o **stallo**) è una condizione in cui _un insieme di [[Processo|processi]] in [[Esecuzione concorrente|esecuzione concorrente]] è bloccato dallo stato dei processi stesso_.

L'assenza di deadlock è considerata una [[Proprietà safety|proprietà safety]] (anche se potrebbe essere più di [[Proprietà liveness|liveness]]).

## Condizioni
Le condizioni sufficienti e necessarie affinche' un deadlock si presenti nel [[Sistema operativo|sistema operativo]] sono:
- **[[Mutua esclusione|mutua esclusione]]** --> le [[Risorsa|risorse]] coinvolte _non devono essere condivisibili_;
- **assenza di preemption** --> le risorse _non devono essere prerilasciabili_;
- **hold and wait** --> le _richieste devono essere bloccanti_;
- **attesa circolare** --> esiste una sequenza di processi $P_{0}, \cdots, P_{n}$ tali per cui $P_{0}$ attende una risorsa assegnata a $P_{1}$, e $P_{1}$ attende una risorsa assegnata a $P_{2}$, ..., e $P_{n}$ attende una risorsa assegnata a $P_{0}$.

## Gestione
I metodi di gestione dei deadlock sono:
- [[Deadlock detection|detection]] + [[Deadlock recovery|recovery]]
- [[Deadlock prevention|prevention]]
- [[Deadlock avoidance|avoidance]]

Un'altra gestione possibile (ma sconsigliata) e' l'_algoritmo dello struzzo_: ignorare la possibilita' dei deadlock!

## Soluzione
L'unica soluzione in caso di deadlock nei sistemi reali è di _uccidere uno dei processi bloccanti_.

## Referenze
- si crea una sorta di [[Equilibrio di Nash|equilibrio di Nash]]
- [[Grafo di Holt]]