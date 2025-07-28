---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 13:35:37
links:
  - "[[Lecture 15042025152135]]"
---
# 64-QAM
---
## Introduzione
> Il **64-QAM (Quadrature Amplitude Modulation)** è una sottotecnica [[QAM]], che introduce una sorta di _gerarchia_ nella [[Modulazione|modulazione]], consentendo di trasmettere _6 bit per simbolo_ attraverso una combinazione di variazioni di ampiezza e fase del segnale portante, ma garantendo soprattutto una _differenza di priorita' dei bit inviati_.

## Tecnica
Nel dettaglio, avviene che ogni simbolo codifica 6 bit, per un totale di 64 simboli distinti. Ma questi simboli sono divisi nei 4 quadranti, in "gray clouds":
![[64-qam-diagramma.png]]

I **quadranti identificano quindi i 2 bit piu' significativi**, di priorita' piu' alta (astraendosi a [[QPSK]]); mentre i **16 simboli all'interno di ogni quadrante identificano i 4 bit meno significativi**, di priorita' piu' bassa.

In questa maniera:
- se il _canale e' pulito_ --> tutti i simboli sono ricevuti con precisione, identificando correttamente i 6 bit;
- se il _canale e' rumoroso_ --> i 2 bit piu' significativi sono ricevuti correttamente, mentre i 4 bit meno significativi potrebbero essere sbagliati.

Questo e' incredibilmente utile per **applicazioni che trasmettono dati di priorita' diversa**, come ad esempio le videochiamate:
- la traccia audio e' importante, quindi i dati sono codificati con i 2 bit piu' significativi;
- la traccia video e' meno importante, quindi i dati sono codificati con i 4 bit meno significativi.

Se per esempio si hanno le 2 seguenti tracce:
- audio = `10 01 11 00`;
- video = `0010 1001 1100 0101`;

allora i bit inviati in 64-QAM saranno il _merge_ dei due: `100010 011001 111100 000101`.

## Referenze