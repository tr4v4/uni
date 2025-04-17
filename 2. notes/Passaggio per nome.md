---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 17:26:07
links:
  - "[[Lecture 12032025111631]]"
---
# Passaggio per nome
---
## Introduzione
> Nel **passaggio per nome** all'[[Invocazione di procedura|invocazione]] della [[Funzione informatica|funzione]] viene prima sostituito in tutte le occorrenze del parametro formale il parametro attuale, e poi viene eseguita normalmente la funzione (si chiama anche _regola di copia_).

Di base si tratta di una rivisitazione della _macro espansione_ di [[Assembly|assembly]]: quando c'è una macro, l'assemblatore al posto del nome della macro ci mette il suo corpo.

## Conflitti
Si tratta, apparentemente, di una _semplice sostituzione sintattica al momento della chiamata di procedura_. Ma nella realta' non e' proprio cosi' semplice. Si pensi al seguente caso:
```C
int y;

void fie (name int x) {
	int y;
	x = x + 1;
	y = 0;
}

y = 1;
fie(y);
```

In questo caso si ha un _conflitto nel corpo di `fie` sulle `y`_: si vanno a confondere le variabili locali di `fie` (`int y`) con i parametri formali sostituiti sintatticamente da quelli attuali (`y`).

### Soluzione
Questo problema si risolve mediante la [[Chiusura|chiusura]]: nel passaggio per nome si passa la chiusura `<exp, amb>`, dove `exp` e' il parametro attuale e `amb` e' l'[[Ambiente|ambiente]] in cui viene valutato (in [[Scope statico|scope statico]]). In questo modo si distinguono variabili che appartengono ad ambienti diversi e si evita il conflitto.

Ogni volta che si fa riferimento quindi al parametro formale passato per nome, si valuta `exp` in `amb`.
![[passaggio-per-nome-chiusura.png]]

## Referenze