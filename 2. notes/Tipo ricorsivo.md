---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 23-09-2025 17:10:09
links:
  - "[[Lecture 09042025110710]]"
---
# Tipo ricorsivo
---
## Introduzione
> I [[Tipi di dato|tipi di dato]] [[Tipi composti|composti]] **ricorsivi** sono _tipi che nella loro definizioni contengono loro stessi_.

Anche se da un punto di vista astratto/logico non hanno alcun senso[^1], i tipi ricorsivi sono _estremamente utili per definire [[Strutture dati|strutture dati]] modificabili dinamicamente_, come [[Lista|liste]], [[Albero informatico|alberi]], ecc...

Si esprimono, di solito, attraverso i [[Tipo prodotto|tipi prodotto]]. Ma si possono anche esprimere attraverso i [[Tipo somma|tipi somma]] (per evitare di dover scrivere il `NULL` per indicare la fine).

Esempio in [[Java]] con le `sealed` classes:
```Java
sealed class IntList permits IntList.Cons, IntList.End {
	static class Cons extends IntList {
		int n; IntList cons;
		Cons( int n, IntList cons ) {…}
	}
	static class End extends IntList {
		End() {}
	}
}

IntList l = new IntList.Cons(1,
			new IntList.Cons(2,
			new IntList.Cons(3,
			new IntList.End())));
```

## Referenze

[^1]: manca il caso base!
