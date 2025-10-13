---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2025 18:47:29
links:
  - "[[Lecture 30042025110449]]"
---
# Tombstones
---
## Introduzione
> Per **tombstones** si intende una _tecnica usata per gestire i [[Dangling pointer|dangling pointers]]_.

## Funzionamento
Essenzialmente quando si crea un puntatore, questo in realta' punta a una _tombstone_ (lapide) creata, all'inizio segnata come _RIP_ (`NULL`).

Quando al puntatore si assegna un valore, e' in realta' la tombstone a contenere l'indirizzo: **il puntatore riceve l'indirizzo della tombstone**.

Di conseguenza le dereferenziazioni dei puntatori diventano _accessi a due hop_:
1. prima si accede alla tombstone;
2. poi da questa si accede all'oggetto puntato.

Quando la cella che contiene il valore puntato dalla tombstone viene liberata (si esce dallo [[Scope|scope]] della variabile, o viene fatta una `free`), la tombstone diventa _RIP_.

In questo modo, si risolvono i problemi scaturiti dalla duplicazione dei puntatori, ovvero quando due puntatori puntano alla stessa cella. In tal caso, infatti, **la tombstone rimane attiva** (aperta) **finche' l'oggetto da essa puntato** (il reale elemento) **e' allocato**.

### Esempio
```C
{
	char *dp = NULL;
	{
		char c = "a";
		dp = &c;
	}
}
```
![[tombstones.png]]

## Problemi
Seppur semplice, questa tecnica _duplica tutte le dereferenziazioni dei puntatori_, e spende anche tempo nella creazione delle tombstones. Inoltre, dal punto di vista dello spazio, abbiamo bisogno di _una tombstone per ogni puntatore_ (sia per l'heap che per lo stack), _che non siamo in grado di recuperare_! Infatti nell'implementazione standard _non e' previsto un contatore di puntatori che puntano alla tombstone_: rimangono attive per tutta l'esecuzione del programma, con la possibilita' quindi di esaurire lo spazio nel cimitero.

## Referenze