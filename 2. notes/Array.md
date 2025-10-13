---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/algoritmi-e-strutture-dati
  - topic/linguaggi-di-programmazione
date: 17-10-2023 20:06:16
links:
  - "[[Lecture 17102023092609]]"
  - "[[Lecture 18102023091849]]"
  - "[[Lecture 04032024091423]]"
  - "[[Lecture 03042025131202]]"
  - "[[Lecture 09042025110710]]"
---
# Array
---
## Introduzione
Ci sono casi in cui per risolvere un problema informatico la dichiarazione di una serie di variabili non basta. Se dovessimo per esempio fare un programma che calcola la media tra 10 numeri, e quindi 100 o 1000, l'utilizzo diretto di [[Identificatore|identificatori]] risulterebbe inopportuno...

Per questo nascono gli **array**, che si sviluppano come _locazioni contigue di memoria_ associate ad una _cella di partenza_. Le variabili "standard", infatti, sono sparse in [[RAM]], o meglio è il [[Loader|loader]] che al momento dell'esecuzione istanzia le locazioni secondo un ordine suo. Gli array, invece, per poter funzionare richiedono di essere istanziati come locazioni in sequenza.

Infatti, a partire da una locazione base di RAM, in un array le altre sono ricavabili dai cosiddetti **indici**, _in relazione al numero di byte occupato dal [[Tipi di dato|tipo di dato]] dell'array_.

### Esempio
Se abbiamo un array di `int` (che occupano 4 byte l'uno), per riferirci alle celle dovremo _sommare all'indirizzo della cella iniziale 4 (per i byte) per l'indice della cella a cui ci riferiamo_:
- `A + 4 * 0`
- `A + 4 * 1`
- `A + 4 * 2`
- `A + 4 * 3`
- `A + 4 * 4`
- ...

Per un array `double` avremo 8 byte per locazione.

## Definizione
> In definitiva gli array sono [[Strutture dati|strutture dati]] costituite da una sequenza di _elementi omogenei_ accessibili tramite un _indice_; hanno _dimensione fissa_[^2] e soprattutto ha un _costo di accesso costante per tutti gli elementi_: vale a dire che non fa distinzione tra l'accesso alla prima cella e all'ultima.

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

## Tipologie
In realta' esistono molti tipi di array, classificati a seconda della loro chiave in
- _array standard_, che hanno come chiave l'indice dell'elemento a partire da 0;
- _array associativi_ (anche detti [[Dizionario|dizionario]]), che hanno come chiave una stringa o un numero qualunque;

e a seconda della loro struttura in
- _array monodimensionali_, che hanno una sola dimensione, e quindi una sola chiave;
- _array multidimensionali_, che hanno più dimensioni, e quindi più chiavi.

<u>Nota bene</u>: i _linguaggi safe_ **non permettono di accedere a un elemento di un array con un indice negativo o maggiore della lunghezza dell'array stesso**, mentre i _linguaggi unsafe_ (come C) lo permettono, ma il risultato è indefinito. Come gia' visto, questo controllo e' quasi sempre fatto a _run-time_, quindi in [[Tipaggio dinamico|tipaggio dinamico]]. Chiaramente questo controllo ad ogni accesso consuma tempo, ma previene attacchi di [[Buffer overflow|buffer overflow]].

### Array multidimensionali
E' necessario decidere come memorizzare gli array multidimensionali in memoria. Esistono 2 modi:
- _ordine di riga_;
- _ordine di colonna_.

![[array-multidimensionali-memorizzazione.png]]

Il primo e' il piu' comune, perche' gli accessi sequenziali in riga sono piu' comuni di quelli in colonna. Di conseguenza si puo' sfruttare meglio il **principio di localita'** della [[Cache|cache]] per accelerare gli accessi.

## Allocamento
Gli array sono definibili in 3 modalita' differenti:
- **statico**: la dimensione e' fissata a _compile-time_;
- **automatico**: la dimensione e' fissata a _run-time_, ma non e' possibile cambiarla (come nel caso in cui la dimensione dipende dal valore di una variabile);
- **dinamico**: la dimensione non e' fissa, ma e' possibile cambiarla a _run-time_.

Per ognuno di questi 3 modi e' necessario stabilire dei metodi per allocare gli array in memoria.

### Array statico
In questo caso e' sufficiente memorizzare l'array nel [[Record di attivazione|record di attivazione]] dello [[Stack|stack]] del programma. La dimensione dell'array e' nota a _compile-time_, quindi non ci sono problemi di allocazione.

### Array automatico o dinamico
In entrambi questi casi, non abbiamo modo di determinare la dimensione dell'array a _compile-time_, per cui si alloca nell'[[Heap|heap]] del programma. In particolare si tiene nel record di attivazione un descrittore dell'array chiamato **dope vector**, che contiene:
- _puntatore alla locazione del reale array in heap_
- _tipo di elementi_
- _rank_ (dimensione algebrica)
- _lunghezza_
- _estensione in uso_ - quante parti sono realmente usate
- _massima estensione_ - quanta memoria massima e' disponibile
- _stride_ - quanto saltare per accedere alla prossima riga/colonna in caso di array multidimensionali

![[dope-vector.png]]

## Rapporto con funzioni
Se vogliamo utilizzare un array in una [[Funzione informatica|funzione]], passandoglielo come parametro, dovremo **per forza** usare il [[Passaggio per riferimento|passaggio per riferimento]]. Pensandoci bene, _non avrebbe senso copiare tutti i valori dell'array nella sezione di memoria della funzione_[^1].

Gli array _possono essere dichiarati nei parametri formali della funzione come costanti_.

## Referenze
- [[Algoritmo di ordinamento]]

[^1]: lo [[Stack|stack]]!
[^2]: nonostante sia possibile ridimensionarli riallocandoli in una posizione in memoria libera (questo processo ha un costo molto oneroso)