---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 22-09-2024 21:26:12
links:
  - "[[Lecture 17092024110611]]"
---
# Macchina astratta
---
## Introduzione
> Una **macchina astratta** è come una [[Macchina fisica|macchina fisica]], perché ha una sua memoria e una lista di operazioni eseguibili, ma in più è composta da
> - _controllo sequenza_
> - _controllo dati_
> - _gestione memoria_
> 
> per consentire un'attuazione delle istruzioni del suo linguaggio nella macchina al livello inferiore. Il processo di **traduzione** delle operazioni e della memoria è gestito dall'**[[Interprete|interprete]]**.
> Ogni macchina astratta ha un suo [[Linguaggio macchina|linguaggio]].
> Formalmente una macchina astratta e' un _insieme di [[Strutture dati|strutture dati]] e [[Algoritmo|algoritmi]] in grado di memorizzare ed eseguire programmi_.

<u>Nota bene</u>: la macchina $M$ al livello inferiore potrebbe essere un'altra macchina astratta o la macchina fisica (quella al livello più basso $0$).

![[macchina-astratta.png]]

## Gerarchie
Di fatto ogni macchina astratta può basarsi su una macchina astratta di livello più basso e fare da base (offrire servizi) a una macchina astratta di livello più alto. Teoricamente la macchina $M_{i}$ dovrebbe nascondere alla macchina $M_{i+1}$ la macchina $M_{i-1}$.

Nella pratica, la gerarchia di macchine astratte si ritrova in più campi dell'informatica:
- schema "a cipolla" del [[Sistema operativo|sistema operativo]];
- schema di una [[Applicazione web|applicazione web]];
- i protocolli di [[Internet|internet]], come il [[Modello ISO-OSI|modello ISO-OSI]].

## Referenze
- [[Realizzazione di una macchina astratta]]