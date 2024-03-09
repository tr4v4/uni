---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
  - topic/programmazione
date: 06-11-2023 22:09:24
links:
  - "[[Lecture 02112023091408]]"
  - "[[Lecture 22112023134305]]"
---
# Linguaggio di programmazione funzionale
---
## Introduzione
> Un **linguaggio di programmazione funzionale** è un tipo di [[Linguaggio di programmazione|linguaggio di programmazione]] che, a differenza degli [[Linguaggio di programmazione imperativo|imperativi]], si _concentrano sul cosa fare piuttosto che sul come_, demandando al [[Compilatore|compilatore]] il "lavoro sporco".

Si basa sulle [[Funzione informatica|funzioni]], avvicinando il più possibile quelle informatiche a quelle [[Funzione matematica|matematiche]]. Non esistono [[Comandi iterativi|cicli]], [[Memorie|memorie]] né [[Strutture dati|strutture dati]]. Di fatto la maggior parte di questi linguaggi adotta come unico tipo di dato "base" il [[ADT|tipo di dato astratto]].

I più importanti e riconosciuti linguaggi di programmazione funzionale sono:
- [[Haskell]]
- [[OCaml]]
- [[Rust]]

## Definizione di funzioni
Le funzioni, o programmi, nei linguaggi di programmazione funzionali, sono definite nel seguente modo
$$f(\omega_{1}, x_{1}, ..., x_{m}) = \text{corpo}_{1}$$
$$f(\omega_{n}, x_{1}, ..., x_{m}) = \text{corpo}_{n}$$
dove:
- $x_{1}, ..., x_{m}$ sono i _parametri formali_[^1]
- $\omega_{i}$ è l'$i$-esimo _pattern_, ovvero l'i-esima forma che l'ADT su cui si sta lavorando assume, e che identifica quello che la funzione deve restituire (il suo $\text{corpo}$) in base all'input
- $\text{corpo}_{i}$ è l'output al pattern $\omega$ preso come input, e si può ottenere da
	- forme di tipi di dati
	- occorrenze dei parametri formali
	- [[Comandi condizionali|if-then-else]] _inline_ (ovvero tradotte in espressioni)
	- chiamate (ricorsive o no) ad altre funzioni

### Invocazione
L'invocazione di una funzione avviene per mezzo del meccanismo di [[Pattern matching|pattern matching]]. In particolare, _definita una chiamata di funzione per $f$ tale che il pattern $\omega$ faccia match con il pattern definito nella chiamata $E_{0}$_, la chiamata viene riscritta nel $\text{corpo}_{i}$ di $f$ dopo aver:
- sostituito a ogni parametro formale del pattern la soluzione dell'equazione $\omega = E_{0}$
- sostituito a ogni parametro formale $x_{j}$ della funzione il parametro attuale $E_{j}$ specificato nella chiamata

## Caratteristiche
Questi linguaggi si distinguono dagli imperativi per una serie di caratteristiche peculiari. Per esempio:
- _non ci sono assegnamenti_
- _non ci sono cicli_
- _non c'è una gestione a basso livello della [[RAM|memoria]]_ (per esempio dei [[Puntatori|puntatori]], compresa l'allocazione e deallocazione della memoria)[^2]
- _non esiste la randomicità_

Le proprietà, invece, che li contrappongono in modo netto dai linguaggi imperativi sono:
- **purezza** --> sono privi di _side effects_, per cui ad ogni input corrisponde al più un solo output
- **[[Potere espressivo|potenza espressiva]]** --> soddisfa la _[[Turing-completezza]]_, ovvero hanno il massimo livello di espressività, per cui sono in grado di risolvere qualunque problema

## Referenze
[^1]: come per i linguaggi imperativi (es. [[C]]/[[C++]])
[^2]: proprio perché ci si vuole avvicinare il più possibile a una visione astratta