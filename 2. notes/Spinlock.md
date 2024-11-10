---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 02-11-2024 18:27:14
links:
  - "[[Lecture 24102024091305]]"
---
# Spinlock
---
## Introduzione
> Per **spinlock** si intende l'_implementazione di [[Sezione critica|sezioni critiche]] mediante l'utilizzo di istruzioni "speciali"_ che realizzano due azioni come se fossero [[Azione atomica|atomiche]]. Spesso sono usate come soluzione hardware al [[Problema della sezione critica|problema della sezione critica]].

## Istruzioni
Le istruzioni speciali più conosciute sono:
- [[Test&Set|test&set]]
- [[Fetch&Set|fetch&set]]
- [[Compare&Swap|compare&swap]]

Ma è possibile usare _una qualunque sequenza di istruzioni che sia resa atomica lato hardware per realizzare degli spinlock_. Si pensi a `f(x) = <x = x/2; return x>` e all'algoritmo
```C
shared int lock = 2;

process P {
	while (true) {
		do {
			int l = f(lock)
		} while (l != 1);
		[enter cs]
		lock = 2;
		[exit cs]
	}
}
```

## Referenze