---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
  - topic/ingegneria-del-software
date: 11-10-2025 14:22:30
links:
  - "[[Lecture 07052025110754]]"
---
# Tipi di dato astratto
---
## Introduzione
Nei [[Linguaggio di programmazione|linguaggi]] [[Type safety|type safe]] viene creata una sorta di **capsula attorno all'implementazione fisica dei tipi**, per permettere al programmatore di _interagirci solo ed esclusivamente mediante l'interfaccia esposta da quella capsula_. In [[C]], per esempio, che e' weakly-typed, non esiste alcun meccanismo: si puo' accedere direttamente all'implementazione fisica dei tipi e leggerli come se fossero altri tipi.

> Un **tipo di dato astratto** (**ADT**) e' un [[Tipi di dato|tipo di dato]] che definisce i possibili valori che lo compongono (abitanti) e le possibili operazioni che possono agire su questi.

Quindi permettono di definire delle astrazioni da rispettare per proteggere parti del programma l'una dall'altra.

## Composizione
Convenzionalmente un ADT e' costituito da:
- nome del tipo astratto `A`;
- tipo di rappresentazione concreta `T`;
- implementazioni di operazioni per la creazione, l'interrogazione e la manipolazione di valori di tipo `A`;
- un _confine di astrazione_ che racchiude `T` e lo rende accessibile solo attraverso le operazioni;

Non si puo' quindi accedere dall'ADT `A` alla sua rappresentazione concreta `T`.

## Proprieta'
### Information hiding
Proprio come avviene per le [[Interfaccia|interfacce]] di programmazione, anche qui viene stabilito un _contratto_ tra produttore e consumatore, concordando i metodi che il primo espone con quelli che il secondo usa. L'[[Implementazione|implementazione]] non e' contemplata: avviene _information hiding_.

### Indipendenza dalla rappresentazione
Come avviene per il [[Polimorfismo|polimorfismo]] [[Sottotipaggio|di sottotipo]] quando si nasconde il reale sottotipo di un tipo, abbiamo un certo grado di _indipendenza dalla rappresentazione_: i consumatori non notano alcuna differenza su ADT implementati dai produttori in modo diverso.

### Moduli
Sono anche un modo per aggregare il codice, ossia definizione e logica delle operazioni che appartengono allo stesso tipo di dato astratto. Si formano i cosiddetti _[[Package|package]]_.

Concettualmente, _possiamo vedere gli ADT come un caso degenere di un modulo che trasporta un ADT_. Tuttavia, i moduli in realta' esprimono la visibilita' dei dati e delle operazioni in modo piu' fine rispetto agli ADT: _la "capsula" e' "permeabile" a piacere_!

Qui sotto i moduli counter e sc incapsulano rispettivamente l'ADT e l'implementazione:
```Rust
mod counter { pub trait Counter { … } }
mod sc {
	use crate::counter::Counter;
	pub struct SC { … }
	impl Counter for SC { … }
}

use crate::counter::Counter;
use crate::sc:SC;
fn use_counter( c:&mut C ) where C: Counter{ … }
fn main(){ … }
```

## Linguaggi
### Rust
In [[Rust]] gli ADT sono implementati tramite i _trait_. Attraverso di essi _si specificano delle funzionalita' che si possono poi associare a dei tipi reali_: il trait rappresenta il tipo astratto la cui interfaccia da' accesso al tipo concreto, implementando le sue operazioni.
```Rust
trait Counter {
	fn new() -> Self;
	fn get( &self ) -> u32;
	fn inc( &self ) -> Self;
}

struct SC { counter: u32 }

impl Counter for SC {
	fn new() -> Self { SC { counter: 0 } }
	fn get( &self ) -> u32 { self.counter }
	fn inc( &self ) -> Self { SC { counter: self.counter + 1 } }
}

fn use_counter<C>( c: &mut C ) where C: Counter {
	let c = c.inc(c);
	let c = c.inc(c);
	print!( "{}", c.get() );
}

fn main(){ use_counter( &mut SC::new() ) }
```

## Architettura
Nel contesto degli [[Architectural styles|architectural styles]], gli ADT fanno da "manager" dei componenti.

## Referenze
- [[Tipi esistenziali]]