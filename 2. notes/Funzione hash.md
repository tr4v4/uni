---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 24-03-2024 19:43:04
links:
  - "[[Lecture 21032024091145]]"
---
# Funzione hash
---
## Introduzione
> Una **funzione hash** è una [[Funzione matematica|funzione]] $h$ usata da [[Tabella hash|tabelle hash]] che preso in input una chiave $k \in U$ dove $U$ è l'insieme di tutte le possibili chiavi, restituisce un valore $v \in [0, m-1]$, dove $m$ è la grandezza dell'array `T` della tabella hash.

## Proprietà
### Uniformità semplice
> Una funzione hash $h$ deve soddisfare (anche se approssimativamente) la proprietà di **uniformità semplice**, il che significa che deve distribuire uniformemente le chiavi all'interno dell'array `T` negli indici $0, \cdots, m-1$. Di conseguenza ogni indice dev'essere generato con probabilità
> $$\frac{1}{m}$$

Di fatto se alcuni indici sono scelti con maggiore probabilità da $h$ allora si avrà un numero maggiore di [[Collisione hash|collisioni]].

Teoricamente parlando per soddisfare tale proprietà _dovremmo conoscere la distribuzione di probabilità con cui le chiavi sono estratte da $U$_, il che è irrealistico: _sarebbe come prevedere quali nomi di variabili un programmatore sceglierà per il suo codice_. Solo in casi specifici tale distribuzione è nota (si pensi a $h(k) = \lfloor mk \rfloor$ con $k \in U = [0, 1[$).

### Assunzioni probabilistiche
Possiamo definire alcune assunzioni che, anche se concretamente non possono essere tutte soddisfatte, idealmente definiscono un corretto criterio per implementari funzioni hash:
1. _tutte le chiavi sono equiprobabili_ (uniformità semplice) --> ovviamente quasi impossibile da attuare, è necessaria una semplificazione;
2. _la funzione hash può essere calcolata in [[Complessità computazionale|tempo costante]]_ $O(1)$ --> se così non fosse tale codifica dominerebbe il costo delle operazioni della tabella hash, ma ci accontentiamo di hashing sufficientemente veloci;
3. _tutte le chiavi sono valori interi non negativi_ --> vero perché possiamo sempre trasformare una qualsiasi chiave $k$ in un intero;

## Metodi
Tra le funzioni hash che analizziamo si trovano:
- [[Metodo della divisione]]
- [[Metodo della moltiplicazione]]
- [[Metodo della codifica algebrica]]

## Referenze