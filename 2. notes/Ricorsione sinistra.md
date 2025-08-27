---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 19:18:21
links:
  - "[[Lecture 05112024110833]]"
---
# Ricorsione sinistra
---
## Introduzione
> Una produzione ricorsiva sinistra e' del tipo
> $$A \to A\alpha$$
> quindi una [[Grammatiche|grammatica]] e' **ricorsiva sinistra** se $A \implies^{+} A\alpha$ per qualche $A \in NT$ e $\alpha \in (T \cup NT)^{*}$.

## Eliminazione
### Ricorsione sinistra immediata
La ricorsione sinistra immediata e' della forma:
$$A \to A\alpha_{1}| \cdots | A\alpha_{n}| \beta_{1} | \cdots | \beta_{m}$$
in cui quindi si nota che alcune produzioni di $A$ non hanno $A$ come prefisso ($\beta_{1}, \cdots, \beta_{m}$). A quel punto si possono sempre rimpiazzare queste produzioni con:
$$A \to \beta_{1}A'|\cdots|\beta_{m}A' \ \ \ \ \ A' \to \alpha_{1}A'|\cdots|\alpha_{n}A'|\epsilon$$

### Ricorsione sinistra non-immediata
Consideriamo la grammatica $G$
$$S \to Ba|b \ \ \ \ \ B \to Bc|Sc|d$$
e notiamo che c'e' si' ricorsione sinistra immediata ($B \to Bc$), ma anche non immediata ($S \implies Ba \implies Sca$).

Vogliamo allora scrivere un algoritmo che in input prenda una grammatica
- libera;
- senza produzioni-$\epsilon$;
- senza produzioni unitarie;
- con ricorsione sinistra non-immediata;

e in output restituisca una grammatica
- libera;
- senza ricorsione sinistra;
- con possibili produzioni-$\epsilon$.

#### Algoritmo
```R
sia NT = {A1, A2, ..., An} in un ordine fissato;
for i from 1 to n {
	for j from 1 to i-1 {
		sostituisci ogni produzione della forma Ai -> Aja con
		le produzioni Ai -> b1a|...|bka dove Aj -> b1|...|bk
		sono le produzioni correnti per Aj;
	}
	elimina la ricorsione sinistra immediata su Ai;
}
```

L'idea di base dell'algoritmo e' che alla fine, **ogni produzione del tipo $A_{i}\to A_{k}\alpha$ sia tale che $i < k$**, in modo che sia impossibile avere ricorsione sinistra non-immediata (e neanche immediata!).

## Referenze