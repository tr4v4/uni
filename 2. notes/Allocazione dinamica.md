---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 03-05-2025 16:42:33
links:
  - "[[Lecture 20032025151643]]"
---
# Allocazione dinamica
---
## Introduzione
> L'**allocazione dinamica** e' una tecnica di [[Allocazione|allocazione]] della memoria primaria gestita dal [[Sistema operativo|sistema operativo]] che consiste nell'_assegnamento della giusta quantita' di memoria ad ogni [[Processo|processo]] che ne fa richiesta_.

Il [[Gestione della memoria|gestore della memoria]] deve mantenere informazioni sulle zone libere e su quelle occupate della memoria.

## Strutture dati
### Bitmap
La memoria viene divisa in _unita' di allocazione_, ognuna delle quali e' rappresentata da un bit in una _bitmap_ ([[Strutture dati|struttura dati]]). Le unita' libere avranno bit a 0, mentre quelle occupate avranno bit a 1.
![[allocazione-dinamica-bitmap.png]]

La **dimensione dell'unita' di allocazione e' determinante**:
- se troppo piccola, la bitmap occupa troppa memoria;
- se troppo grande, si spreca memoria ([[Frammentazione interna|frammentazione interna]]).

#### Vantaggi
La struttura dati e' compatta, con dimensione fissa calcolabile a priori.

#### Svantaggi
Per cercare uno spazio di memoria di dimensione $k$ unita', _bisogna cercare una sequenza di $k$ "0" consecutivi nella bitmap_. Tale operazione ha [[Complessità computazionale|complessita' computazionale]] $O(m)$, dove $m$ e' il numero di unita' di allocazione.

### Liste con puntatori
Si mantiene una [[Lista|lista]] dei blocchi allocati e liberi di memoria. In particolare, ogni elemento della lista specifica:
- se si tratta di un processo ($P_{i}$) o di un blocco libero ($H$);
- la dimensione (indirizzo di inizio e fine) del blocco.

![[allocazione-dinamica-liste-puntatori.png]]

#### Vantaggi
E' molto comoda, e fare [[Compattazione|compattazione]] diventa ottimale. Inoltre l'allocazione e' facile:
1. tra i blocchi liberi ne viene scelto uno sufficientemente grande;
2. una parte di questo viene allocata al processo, e il resto rimane libero.

Chiaramente se la dimensione del blocco e' uguale a quella del processo, il blocco viene allocato tutto al processo.

#### Svantaggi
La deallocazione non e' cosi' semplice. Infatti ci sono 4 casi possibili:
1. il blocco da liberare e' tra due occupati --> diventa libero e basta;
2. il blocco da liberare ha a destra un blocco libero --> il blocco da liberare e quello a destra vengono uniti;
3. il blocco da liberare ha a sinistra un blocco libero --> il blocco da liberare e quello a sinistra vengono uniti;
4. il blocco da liberare ha sia a destra che a sinistra dei blocchi liberi --> i tre blocchi vengono uniti.

Per farlo in tempo $O(1)$ e' necessario implementarlo con _liste doppiamente concatenate_, il che aggiunge un certo overhead.

### Considerazioni
E' possibile ottimizzare il costo di allocazione mantenendo una lista di blocchi liberi separata ed eventualmente _ordinando tale lista per dimensione_ (in modo da poter applicare una [[Ricerca dicotomica|ricerca binaria]]).

Le informazioni da mantenere sono salvate:
- per i blocchi occupati --> nella tabella dei processi;
- per i blocchi liberi --> nei blocchi stessi.

## Selezione del blocco libero
Le strategie di selezione del blocco libero sono:
- [[First fit]];
- [[Next fit]];
- [[Best fit]];
- [[Worst fit]].

## Referenze