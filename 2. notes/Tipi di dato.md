---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 22-09-2023 18:11:31
links:
  - "[[Lecture 22092023100303]]"
  - "[[Lecture 25092023151613]]"
  - "[[Lecture 02042025112213]]"
---
# Tipi di dato
---
## Introduzione
Il [[Sistema di tipi|sistema di tipi]] e' nato per sfuggire al [[Paradosso di Russell|paradosso di Russell]], definendo un insieme di insiemi un tipo diverso dal semplice insieme.

## Definizione
> Formalmente potremmo definire i **tipi di dato** come _un metodo sintattico praticabile per dimostrare l'assenza di determinati comportamenti del programma, fatto classificando le unità sintattiche in base ai tipi di valore che assumono_.

<u>Nota bene</u>: i comportamenti vietati, per esempio, sono "inserire una stringa in una variabile di tipo intero".

Nella pratica i tipi si interpretano come **collezioni di valori omogenei e rappresentabili**. Tra l'altro l'_omogeneità si riflette anche nel modo in cui sono memorizzati in memoria_, ma per una questione di comodità.

## Proprieta'
I tipi di dato aiutano il programmatore sotto molti aspetti diversi:
- disciplinano l'organizzazione concettuale dei programmi;
- astraggono il programma, implementando le interfacce che associano a un tipo delle operazioni;
- supportano il _type-checking_: usare i tipi per rilevare errori di programmazione
	- si chiama _safety_ del linguaggio: capacità di un linguaggio di garantire l'integrità delle sue astrazioni
	- alcuni linguaggi sono strongly typed (Rust), altri no (C)
- supportano per il refactoring --> se si cambia la dichiarazione del tipo della struttura un passaggio del type checker indicherà tutti i punti in cui il tipo è usato in modo incoerente, per essere corretti;
- supportano anche l'implementazione, l'efficienza quindi nella scrittura del programma ma anche nella sua compilazione ed esecuzione;

## Typing
### Statico vs dinamico
Possiamo distinguere il controllo dei tipi da parte del type-checker in:
- [[Tipaggio statico|tipaggio statico]];
- [[Tipaggio dinamico|tipaggio dinamico]].

<u>Nota bene</u>: non è detto che un linguaggio [[Interprete|interpretato]] debba avere necessariamente tipaggio dinamico, può anche averlo statico.

<u>Nota bene</u>: un tipaggio non esclude l'altro, si possono avere ibridazioni tra i 2 paradigmi.

### Manifest vs inferred
Possiamo distinguere il tipo di tipaggio sulla base della _quantità di informazioni sui tipi che il programmatore deve inserire nei suoi programmi_:
- [[Tipaggio manifest|tipaggio manifest]];
- [[Tipaggio inferred|tipaggio inferred]].

## Tipologie
I tipi di dato si dividono in 2 categorie:
- [[Tipi di base|tipi di base]];
- [[Tipi composti|tipi composti]].

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