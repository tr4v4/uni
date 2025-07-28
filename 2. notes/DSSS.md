---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 11:52:12
links:
  - "[[Lecture 14042025111851]]"
  - "[[Lecture 28042025111320]]"
---
# DSSS
---
## Introduzione
> Il **Direct Sequence Spread Spectrum (DSSS)** è una tecnica di [[Codifiche wireless|codifica wireless]] che utilizza _sequenze di chip per modulare i dati_, migliorando la resistenza alle interferenze e aumentando la sicurezza della trasmissione.

In particolare si usa una **chip sequence**, che rappresenta un bit (0 normale, 1 viene invertita). Questo **chip codifica un singolo bit su tutte le frequenze dell'intervallo**.
![[DSSS.png]]

## Implementazione
Viene fatto lo [[XOR]] tra i bit da trasmettere e la chip sequence, creando il segnale che poi sara' realmente trasmesso.
![[chip-sequence.png]]

Piu' lunghe sono le chip sequence (piu' chip per bit), maggiore sara' la bandwidth utilizzata[^2] (infatti e' spread spectrum, minore throughput), ma piu' robusta sara' la trasmissione: infatti il [[Link budget|link budget]] aumenta, perche' _il segnale ricevuto e' la somma ([[Integrale|integrazione]]) di ogni singolo chip nel tentativo di riconoscere la sequenza_; inoltre il segnale al ricevitore appare come a bassa potenza ma a banda larga, quindi piu' difficile da intercettare e disturbare.

Il DSSS viene spesso implementato in combinazione con [[CDMA]].

## Regole
Le frequenze assegnate al DSSS sono regolate da una serie di calcoli sulla sovrapposizione di frequenze: lo standard IEEE 802.11b definisce 11 canali di frequenza di cui pero' **realmente 3** (1, 6, 11) **sono utilizzabili contemporaneamente a distanza ravvicinata**, per evitare interferenze tra loro.

Infatti la distanza tra questi 3 canali (25MHz) e' tale da garantire che non ci siano sovrapposizioni di canali. Se si vogliono usare piu' canali, allora si devono mantenere le rispettive potenze di trasmissione entro i limiti di seguito definiti:
![[DSSS-frequency.png]]

Di fatto, se si usano canali diversi da 1, 6 e 11, con potenza superiore, si rischiano interferenze tra i canali:
![[DSSS-frequency-interference.png]]

## Difficolta'
La difficoltà principale nella _creazione di chip sequence_ è che **devono essere statisticamente riconoscibili anche se combinate tra loro**, per evitare interferenze e garantire una corretta ricezione.

Esistono algoritmi per generare chip sequence che soddisfano questi requisiti, come il _Gold code_ e il _Kasami code_.

Piu' lunghi sono i chip, maggiore e' la probabilita' di riconoscere la sequenza di arrivo, anche con interferenze[^1].

## Referenze

[^1]: riconoscere la skyline...
[^2]: questo e' fondamentale! Serve aumentare lo spettro per poter riconoscere piu' fedelmente i singoli chip.
