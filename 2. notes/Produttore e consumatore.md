---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 20-11-2024 23:06:10
links:
  - "[[Lecture 07112024092537]]"
---
# Produttore e consumatore
---
## Introduzione
> Il problema del **produttore e consumatore** è uno dei [[Problemi classici della programmazione concorrente|problemi classici della programmazione concorrente]]. Consiste nell'interazione tra due processi, un _produttore_ e un _consumatore_, che devono condividere una variabile tale che il primo la modifica e il secondo la legge rispettando le seguenti proprietà:
> - il _producer non deve scrivere nuovamente l'area di memoria condivisa prima che consumer abbia effettivamente utilizzato il valore precedente_[^1];
> - il _consumer non deve leggere due volte lo stesso valore, ma attendere che il producer abbia generato il successivo_[^1];
> - assenza di [[Deadlock|deadlock]];
> - assenza di [[Starvation|starvation]].

## Implementazione
Il problema si può facilmente risolvere attraverso l'impiego di [[Semafori|semafori]]:
```C
shared Object buffer;
Semaphore empty = new Semaphore(1);
Semaphore full = new Semaphore(0);

process Producer {
  while (true) {
	Object val = produce();
    empty.P();
    buffer = val;
    full.V();
  }
}

process Consumer {
  while (true) {
    full.P();
    Object val = buffer;
    empty.V();
    consume(val);
  }
}
```

<u>Nota bene</u>: _anche se ci fossero più produttori e più consumatori funzionerebbe ugualmente_, semplicemente solo un produttore o un consumatore accederebbe al `buffer` alla volta, e gli altri sarebbero in attesa rispettivamente nella coda di `empty` (`P`) e nella coda di `full` (`P`).

Infatti, se consideriamo un solo produttore e un solo consumatore, ha poco senso usare i semafori: _si tratta di una stretta alternanza tra i due processi_. I semafori hanno senso dal momento in cui entrano in gioco più produttori e più consumatori, perché è necessario garantire che un solo produttore o consumatore acceda al `buffer` alla volta, e allo stesso tempo assenza di starvation (semafori [[FIFO]]!).

## Referenze
[^1]: delle sorte di [[Race condition|race condition]]