---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 30-11-2023 15:17:13
links:
  - "[[Lecture 23112023091708]]"
---
# Ricorsione strutturale
---
## Introduzione
> La **ricorsione strutturale** consiste in un _approccio sistematico alla risoluzione di problemi per mezzo della [[Ricorsione|ricorsione]]_, con l'imposizione di _vincoli implementativi_.

Se pensiamo a un problema definito su di un [[ADT|tipo di dato algebrico]], si ha:
- _caso atomico_, in cui la soluzione al problema è _diretta_
- _caso composto_, in cui si risolve prima il problema sulle componenti del dato algebrico (con la ricorsione), e poi si sintetizza la risposta per il caso composto assumendo che la chiamata ricorsiva abbia returnato la soluzione corretta (_uniformità della soluzione_)

## Definizione
> Una funzione $f$ è definita per ricorsione strutturale sse:
> - $f$ considera come pattern _tutte le forme del dato una e una sola volta_;
> - $f$ si richiama ricorsivamente passando come _primo parametro attuale solo uno dei parametri formali contenuti nel pattern_;
[^1]

La prima proprietà significa che per ogni forma del dato algebrico ($\omega$) del problema si ha una soluzione ($\text{corpo}$) associata[^2].

La seconda proprietà garantisce che il programma termini, e quindi _non diverga_: la funzione infatti si richiama su input sempre più piccoli, arrivando alla fine al caso base/atomico, risolvibile direttamente.

### Esempio
Prendiamo come dato algebrico la lista di numeri naturali, definita quindi come
$$\mathbb{L} ::= [] \ | \ \mathbb{N} :: \mathbb{L}$$

Il programma definito per ricorsione strutturale che calcola la somma di tutti gli elementi della lista sarà allora:
```hs
sum [] = 0
sum (x:xs) = x + sum xs
```

## Teoremi
I teoremi fondamentali della ricorsione strutturale sono:
1. **tutte le funzioni definite per ricorsione strutturale convergono su ogni input**
2. **ci sono problemi risolvibili con la ricorsione generale ma non con la ricorsione strutturale**, casi rarissimi che studieremo in _informatica teorica_

## Dimostrazione
Per dimostrare determinate proprietà di una funzione definita per ricorsione strutturale si usa l'[[Induzione strutturale|induzione strutturale]].

## Referenze
[^1]: l'idea di scomporre il problema in sottoproblemi più semplici da risolvere è in linea con l'[[Approccio top-down|approccio top-down]]
[^2]: dove $\omega$ e $\text{corpo}$ sono parte della [[Linguaggio di programmazione funzionale#Definizione di funzioni|definizione di funzione dei linguaggi funzionali]]