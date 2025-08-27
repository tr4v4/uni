---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 19:20:10
links:
  - "[[Lecture 05112024110833]]"
---
# Fattorizzazione a sinistra
---
## Introduzione
> La **fattorizzazione a sinistra** di una [[Grammatiche|grammatica]] (di solito [[Grammatiche libere|libera]]) e' fondamentale nei [[Parser top-down|top-down parser]] per _risolvere casi di nondeterminismo_.

Prendiamo per esempio queste produzioni di una grammatica $G$
$$A \to aBbc|aBd$$
Ci accorgiamo che se sulla pila leggo $A$, in un top-down parser, non sono in grado di determinare quale produzione scegliere (neanche con [[Look-ahead|look-ahead]]!). Ma con una semplice fattorizzazione del tipo
$$A \to aBA' \ \ \ \ \ A' \to bc | d$$
riesco a togliere il nondeterminismo!

## Algoritmo
```R
inizializza N=NT;
ripeti il ciclo finche' nessuna modifica e' piu' possibile a N o all'insieme delle produzioni {
	for each A in N {
		sia a il prefisso piu' lungo comune alle parti destre di alcune
		produzioni di A;
		if a != epsilon {
			sia A' un nuovo nonterminale (N = N u {A'});
			rimpiazza tutte le produzioni per A
				A -> ab1|...|abk|y1|...|yh
			con
				A -> aA'|y1|...|yh
				A' -> b1|...|bk
		}
	}
}
```

### Esempio
La grammatica
$$E \to T | T+E | T-E \ \ \ \ \ T \to A|A*T \ \ \ \ \ A \to a|b|(E)$$
puo' essere fattorizzata in
$$E \to TE' \ \ \ \ \ E' \to \epsilon|+E|-E \ \ \ \ \ T \to AT' \ \ \ \ \ T' \to \epsilon|*T \ \ \ \ \ A \to a|b|(E)$$


## Referenze