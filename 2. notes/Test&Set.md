---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 02-11-2024 18:33:05
links:
  - "[[Lecture 24102024091305]]"
---
# Test&Set
---
## Introduzione
> **Test&Set** è un'istruzione hardware usata per realizzare lo [[Spinlock|spinlock]], ovvero [[Sezione critica|sezioni critiche]].

## Istruzione
L'istruzione `test&set` in sé, fornita dalla CPU, esegue la seguente istruzione come se fosse un'[[Azione atomica|azione atomica]]: `TS(x, y) := <y = x; x = 1>`.
Quindi, in poche parole, assegna a `y` il valore di `x`, e poi setta `x` a `1`.

## Algoritmo
Si può sfruttare quest'istruzione per risolvere quasi il [[Problema della sezione critica|problema della sezione critica]]:
```C
shared int lock = 0;

process P {
	int vp;
	while (true) {
		do {
			TS(lock, vp);
		} while (vp);
		[enter cs]
		lock = 0;
		[exit cs]
	}
}

process Q {
	int vq;
	while (true) {
		do {
			TS(lock, vq);
		} while (vq);
		[enter cs]
		lock = 0;
		[exit cs]
	}
}
```

Con poco sforzo si dimostra che viene garantita [[Mutua esclusione|mutua esclusione]], assenza di [[Deadlock|deadlock]], assenza di delay non necessari ma _non l'assenza di [[Starvation|starvation]]_[^1].

## Referenze
[^1]: per via dell'[[Assioma di finite progress|assioma di finite progress]]