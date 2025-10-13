---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 06-04-2025 12:56:59
links:
  - "[[Lecture 02042025112213]]"
---
# Tipi di base
---
## Introduzione
> I **tipi di base** sono i [[Tipi di dato|tipi]] fondamentali di un [[Linguaggio di programmazione|linguaggio di programmazione]].

Di solito comprendono:
- _numeri interi_ --> `int`;
- _numeri reali_ --> `double` o `float`;
- _caratteri_ --> `char`.

Ma in realta' si estendono a:
- _unita'_ --> `void` o `()`;
- _booleani_ --> `bool`;
- _enum_ --> `enum`;

## Tipi
### Int
Caratteristiche principali:
- una variabile intera contiene un valore intero ($n \in \mathbb{Z}$)
- in memoria un intero occupa _4 byte_, con cui è possibile rappresentare $2^{16}$ numeri
	- da -2 miliardi a +2 miliardi
- le operazioni aritmetiche sugli interi sono: +, -, /, \*, %, `abs()`
	- %
		- si può ricavare con `r = n - (n/d)*d`, ma è meglio sfruttare l'operatore predefinito perché più efficiente
		- il risultato di numeri negativi dipende dal compilatore
	- /
		- tra interi produce solo il quoziente
		- se il divisore è 0 produce un errore
- le operazioni di confronto sugli interi sono: >, \==, !=, ...

### Double
Caratteristiche principali:
- una variabile reale contiene un valore reale ($n \in \mathbb{R}$)
- in memoria un reale occupa _8 byte_
- si possono scrivere nei seguenti modi
	- `3.1415`
	- `.000016`
	- `120.`
	- `31.415e-1`
	- `0.16E-4`
	- `12e1`
- le operazioni della libreria `cmath` che lavorano con i reali sono: `pow()`, `log()`, `sqrt()`
- <u>attenzione</u> alla _precisione_

### Float
Si faccia riferimento alla [[Codifica floating-point|codifica floating-point]].

### Char
Caratteristiche principali:
- in memoria un carattere occupa _1 byte_
- valori racchiusi tra singoli apici (`''`)
- notazione da tabella [[ASCII]]
- operazioni: qualunque operazione tra interi, perché ad ogni carattere corrisponde un codice numerico (indice della tabella ASCII)

### Bool
Caratteristiche principali:
- valori booleani: `true` o `false` (convertiti rispettivamente in 1 e 0)
- un booleano occupa _1 bit_
- operazioni:
	- `&&` = [[AND]]
	- `||` = [[OR]]
	- `!` = [[NOT]]

### Unit
Caratteristiche principali:
- contiene solo il singoletto `()`
- è circa la stessa cosa che fa il `void`, ma per i linguaggi funzionali
- viene usato in entrambi i paradigmi come _tipo di ritorno di una funzione che non restituisce alcun valore_
- la differenza concettuale sta nel fatto che nel `void` non ci sono proprio abitanti, quindi non può essere passato come parametro, a differenza di Unit

### Enum
Caratteristiche principali:
- si tratta di una enumerazione finita di costanti associate a un tipo definito come `enum`
- per esempio `enum RogueOne { Jyn, Cassian, Chirrut, K2SO, Bodhi, Baze }` definisce un tipo `RogueOne` con i suoi abitanti tale che 
	- `Jyn` = 0
	- `Cassian` = 1
	- `Chirrut` = 2
	- `K2SO` = 3
	- `Bodhi` = 4
	- `Baze` = 5
- quindi aumentano la leggibilita' e permettono al controllo di tipo di verificare che una variabile con enumerazione assuma solo i valori corretti
- tuttavia non tutti i linguaggi implementano gli `enum` in modo sicuro (safe), ossia non permettendo di usare un `enum` come un intero
	- si pensi a `C`, dove `enum` e' solo _zucchero sintattico_ per `typedef int RogueOne; const RogueOne Jyn=0, Cassian=1, ...;`

## Osservazione
Gli `enum` a differenza degli altri tipi di base, _non sono definiti mediante predicati che definiscono la loro appartenenza ad alcuni valori possibili, ma elencando i possibili abitanti di quel tipo_. Di fatto:
- `enum` --> [[Tipo estensionale|tipo estensionale]];
- `int`, `float`, `char`, `bool`, `unit` --> [[Tipo intensionale|tipo intensionale]].

Si potrebbe dire che `enum` e' un _meta-tipo_!

## Referenze