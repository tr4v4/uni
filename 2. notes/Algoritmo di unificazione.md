---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 16:00:32
links:
  - "[[Lecture 16042025110927]]"
---
# Algoritmo di unificazione
---
## Introduzione
> L'**algoritmo di unificazione** e' l'_[[Algoritmo|algoritmo]] usato per fare [[Inferenza di tipo|inferenza di tipo]]_.

## Algoritmo
```R
unify(C) {
	if C == then []
	else
		let { S = T } C’ = C
		if S == T
			unify(C’)
		else if isVar(S) && S !in FV(T)
			unify([S -> T]C’) * [S -> T]
		else if isVar(T) && T !in FV(S)
			unify([T -> S]C’) * [T -> S]
		else if S == S1 -> S2 && T == T1 -> T2
			unify(C’ U {S1 = T1, S2 = T2})
		else
			fail
}
```

dove:
- $C$ e' l'insieme delle equazioni di tipo che derivano dall'analisi del codice del programma;
	- per esempio $X = 5$ produce l'equazione $X = \text{Nat}$;
- $[X \to T]$ significa "rimpiazzare $X$ con $T$";
	- per esempio $[X \to T](X = \text{Nat})$ produce $T = \text{Nat}$;
- $A * B$ e' un operatore di composizione di sostituzione del tipo;
	- in particolare $A * B = [X \to A(T) \ \ \forall (X \to T) \in B] \cup [X \to T \ \ \forall (X \to T) \in A, X \notin dom(B)]$ dove $A(T) = T$ se $T \notin dom(A)$ e $A(X \to Y) = A(X) \to A(Y)$;
- $FV(X)$ e' la funzione di [[Variabile libera|variabile libera]].

## Referenze