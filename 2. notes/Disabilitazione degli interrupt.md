---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 02-11-2024 18:21:27
links:
  - "[[Lecture 24102024091305]]"
---
# Disabilitazione degli interrupt
---
## Introduzione
> La **disabilitazione degli interrupt** è una tecnica hardware usata per risolvere il [[Problema della sezione critica|problema della sezione critica]].

## Idea
Nei [[CPU|processori]] single-core, i [[Processo|processi]] [[Esecuzione concorrente|concorrenti]] vengono "alternati" tramite il meccanismo degli [[Interrupt|interrupt]]. Allora possiamo _realizzare le [[Sezione critica|sezioni critiche]] disabilitando gli interrupt e riattivandoli subito dopo_. In questo modo un processo nella CS non potrà essere interrotto da altri processi.

## Algoritmo
```C
process P {
	while (true) {
		[disable interrupt]
		[enter cs]
		[enable interrupt]
		[exit cs]
	}
}
```

## Problemi
I problemi di questa tecnica sono i seguenti:
- _funziona solo su macchine single-core_ (non è possibile disabilitare gli interrupt di più core);
- _riduce il grado di parallelismo del processore_;
- _il [[Sistema operativo|SO]] deve lasciare ai processi la responsabilità di riattivare gli interrupt_ (pericoloso).

## Referenze