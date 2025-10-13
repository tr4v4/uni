---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
  - topic/linguaggi-di-programmazione
date: 28-11-2023 20:27:42
links:
  - "[[Lecture 22112023134305]]"
  - "[[Lecture 09042025110710]]"
---
# Pattern matching
---
## Introduzione
> Il **pattern matching**, nel contesto dell'invocazione di una [[Funzione informatica|funzione]] in un [[Linguaggio di programmazione funzionale|linguaggio di programmazione funzionale]] consiste nell'_operazione di riconoscimento del pattern $\omega$ della funzione $f$ e nella conseguente [[Sostituzione|sostituzione]] di tutti i parametri formali di $\omega$ nelle sotto-espressioni di $f$_.

Per esempio, preso il pattern
$$(x, y)$$
esso fa match con
$$(O::[], tt)$$
per mezzo della sostituzione
$$[(O::t)/x, tt/y]$$

## Funzionamento
Nel contesto dei [[Linguaggio di programmazione|linguaggi di programmazione]] in generale (non solo funzionali), il pattern matching _individua e controlla elementi specifici rispetto a un certo schema_.

In particolare, nei [[Tipo prodotto|tipi prodotto]] e' fondamentale per destrutturarli:
```Rust
struct Person { name: [ char; 3 ], age: i32 };
struct PersonR { name: [ char; 3 ], age: [ char; 4 ] };

let eva = Person { name: ['E','v','a'], age: 25 };
let Person{ name, age } = eva;     // implicit pattern-matching
let evaR = PersonR{ name, age: match age {
		1..=10 => [ 'K','i','d','' ],
		11..=20 => [ 'T','e','e','n' ],
		_ => [ 'O', 'l', 'd', '' ]
	}
};
```

## Referenze