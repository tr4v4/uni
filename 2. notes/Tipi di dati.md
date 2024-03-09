---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
date: 22-09-2023 18:11:31
links:
  - "[[Lecture 22092023100303]]"
  - "[[Lecture 25092023151613]]"
---
# Tipi di dati
---
## Tipologie
Gli [[Identificatore|identificatori]] sono associati ad un tipo di dato, che ne determina l'insieme di operazioni che possono essere svolte su di esso. I principali tipi di dati sono:
- `int`
- `double`
- `char`
- `bool`

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
- una variabile reale contiene un valore reale ($n \in {R}$)
- in memoria un reale occupa _8 byte_
- si possono scrivere nei seguenti modi
	- `3.1415`
	- `.000016`
	- `120.`
	- `31.415e-1`
	- `0.16E-4`
	- `12e1`
- le operazioni della libreria `cmath` che lavorano con i reale sono: `pow()`, `log()`, `sqrt()`
- <u>attenzione</u> alla _precisione_

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

## Casting
Il **casting** è l'operazione di conversione di una variabile da un tipo a un altro. In particolare il casting si può presentare _implicitamente_ o _esplicitamente_. Quindi:
- cast implicito
	- $\mathbb{Z}$ --> $\mathbb{R}$: quando ci sono operazioni tra reali e interi o di soli reali
	- $\mathbb{R}$ --> $\mathbb{Z}$: quando viene preso in ingresso (`cin`) un numero reale da assegnare a una variabile intera; _troncamento della parte reale_
- cast esplicito
	- $\mathbb{Z}$ --> $\mathbb{R}$: `(double)4` = `4.0`
	- $\mathbb{R}$ --> $\mathbb{Z}$: `(int)4.6` = `4`

### Regola fondamentale
$$\forall X \in E, (\exists X \in \mathbb{R} \implies E \subseteq \mathbb{R})$$
ovvero
> Se all'interno di un espressione esiste almeno una variabile reale, allora tutte le altre variabili dell'espressione verranno convertite in reali.

Questa regola va in completo accordo con il [[Type safety|type safety]], un principio da rispettare per una programmazione pulita e precisa.
## Referenze