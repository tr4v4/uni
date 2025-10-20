---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 20-10-2025 13:05:32
links:
  - "[[Lecture 17102025151336]]"
---
# Indice
---
## Introduzione
> Un'**indice** in [[SQL]] e' uno _strumento potente per rendere piu' veloce l'esecuzione delle query_.

Si realizzano per mezzo di [[Funzione hash|hashing]] e altre [[Struttura dati|strutture dati]] (come gli [[Albero|alberi]]).

<u>Nota bene</u>: sono definiti a livello fisico del [[DBMS]] (guardare [[Architettura di un DBMS|architettura di un DBMS]]), non logico! Nonostante cio', gli sviluppatori di SQL _hanno pensato che fosse meglio dare la possibilita' ai programmatori di specificare al livello logico la presenza di indici_. In questo modo puo' favorire l'accesso su certi dati.

## Sintassi
Fondamentalmente funzionano creando degli indici da associare a dei campi di alcune tabelle/relazioni. Una volta che e' stato creato l'indice, **il tempo di risposta per l'attivita' di ricerca dei dati diminuisce notevolmente**.
```SQL
CREATE INDEX idx_Surname ON OFFICER(Surname)
```

<u>Attenzione</u>: **rimane comunque da considerare il tempo di creazione dell'indice**! Anche se si tratta di una cosa che si fa _una tantum_...

## Realta'
Oggi, in realta', **molti DBMS costruiscono in fase di ottimizzazione delle query degli indici automaticamente**.

## Referenze