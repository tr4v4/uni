---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/algoritmi-e-strutture-dati
date: 17-10-2023 20:06:16
links:
  - "[[Lecture 17102023092609]]"
  - "[[Lecture 18102023091849]]"
  - "[[Lecture 04032024091423]]"
---
# Array
---
## Introduzione
Ci sono casi in cui per risolvere un problema informatico la dichiarazione di una serie di variabili non basta. Se dovessimo per esempio fare un programma che calcola la media tra 10 numeri, e quindi 100 o 1000, l'utilizzo diretto di [[Identificatore|identificatori]] risulterebbe inopportuno...

Per questo nascono gli **array**, che si sviluppano come _locazioni contigue di memoria_ associate ad una _cella di partenza_. Le variabili "standard", infatti, sono sparse in [[RAM]], o meglio è il [[Loader|loader]] che al momento dell'esecuzione istanzia le locazioni secondo un ordine suo. Gli array, invece, per poter funzionare richiedono di essere istanziati come locazioni in sequenza.

Infatti, a partire da una locazione base di RAM, in un array le altre sono ricavabili dai cosiddetti **indici**, _in relazione al numero di byte occupato dal [[Tipi di dati|tipo di dato]] dell'array_.

### Esempio
Se abbiamo un array di `int` (che occupano 4 byte l'uno), per riferirci alle celle dovremo _sommare all'indirizzo della cella iniziale 4 (per i byte) per l'indice della cella a cui ci riferiamo_:
- `A + 4 * 0`
- `A + 4 * 1`
- `A + 4 * 2`
- `A + 4 * 3`
- `A + 4 * 4`
- ...

Per un array `double` avremo 8 byte per locazione.

## Caratteristiche
In definitiva gli array sono [[Strutture dati|strutture dati]] costituite da una sequenza di _elementi omogenei_ accessibili tramite un _indice_; hanno _dimensione fissa_[^2] e soprattutto ha un _costo di accesso costante per tutti gli elementi_: vale a dire che non fa distinzione tra l'accesso alla prima cella e all'ultima.

## Sintassi
### Dichiarazione
Per dichiarare un array si utilizza la sintassi:
> `type name[length];`

quindi:
- `int A[20];`
- `char ciao[5];`
- ...

<u>Attenzione</u>: la _lunghezza di un array_ conviene _definirla con delle costanti_ piuttosto che scrivere il numero diretto.

Non esistono, inoltre, lunghezze di array variabili: per ora **gli array sono strutture dati statiche** (che perciò non mutano di dimensione in _runtime_).

### Accesso agli elementi
Per accedere a un elemento di un array si utilizzano gli _indici_, che vanno da `0` a `length-1`.

## Rapporto con funzioni
Se vogliamo utilizzare un array in una [[Funzione informatica|funzione]], passandoglielo come parametro, dovremo **per forza** usare il [[Passaggio per riferimento|passaggio per riferimento]]. Pensandoci bene, _non avrebbe senso copiare tutti i valori dell'array nella sezione di memoria della funzione_[^1].

Gli array _possono essere dichiarati nei parametri formali della funzione come costanti_.

## Referenze
- [[Algoritmo di ordinamento]]

[^1]: lo [[Stack|stack]]!
[^2]: nonostante sia possibile ridimensionarli riallocandoli in una posizione in memoria libera (questo processo ha un costo molto oneroso)