---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 02-10-2023 21:16:00
links:
  - "[[Lecture 02102023151814]]"
  - "[[Lecture 03102023091610]]"
  - "[[Lecture 06102023094618]]"
  - "[[Lecture 05032025111458]]"
---
# Iterazione
---
## Introduzione
Anche detti **cicli**, essi sono utilizzati quando si vuole fare una stessa operazione per un numero determinato (_for_) o indeterminato (_while_) di volte.

## Tipologie
### For
Sintassi: `for (variable=expression; condition; expression) statement`, dove
- _variable_ --> [[Identificatore|identificatore]] che funge da controllore/contatore del ciclo
- _condition_ --> [[Comandi condizionali|condizione]] di ripetizione del ciclo
- _expression_ --> [[Espressione|espressione]] di modifica di _variable_
- _statement_ --> gruppo di [[Istruzione|istruzioni]]

Il ciclo `for` è un particolare tipo di ciclo che compatta una serie di istruzioni e controlli. Può facilmente essere ricreato con un `while`, ma a differenza di quest'ultimo:
> Il **for** viene utilizzato per cicli di cui si sa determinare con precisione per quante volte saranno eseguiti.

Infatti non posso modificare _indice_, _inizio_, _fine_ e _passo_ del `for` all'interno del suo corpo: questo perché **dev'essere sempre possibile determinare quanti cicli ci saranno a run-time** (non compile-time).

<u>Nota bene</u>: di fatto il `for` del [[C]] viene tradotto in un costrutto di iterazione indeterminata (`while`).

#### Es
Esempio in [[C++]]
```cpp
int main() {
	for (int i=0; i<10; i++) {
		cout << "ciao" << endl;
	}
	return 0;
}
```

#### Limiti
Con questo tipo di iterazione:
- _non posso non terminare_ --> un qualunque programma con [[Assegnamento|assegnamento]], `if` e `for` termina sempre;
- _non posso esprimere neanche tutti i programmi che terminano_ --> si pensi alla [funzione di Ackermann](https://it.wikipedia.org/wiki/Funzione_di_Ackermann).

<u>Nota bene</u>: con l'aggiunta del `goto` otterrei la [[Turing-completezza|Turing-completezza]].

#### Semantica
1. valuta le espressioni `inizio` e `fine`, "congelando" i valori ottenuti (non sono più modificabili)
2. inizializza `indice` con il valore di `inizio`
3. se `indice > fine` termina l'esecuzione del `for`; altrimenti
	- si esegue corpo e si incrementa `indice` del valore di `passo`
	- si torna al punto 3

<u>Attenzione</u>: con questa semantica il `for` funziona solo per indici e passi positivi; c'è un'altra implementazione per estendere il `for` a indici e passi negativi.

### While
Sintassi: `while (condition) statement`, dove
- _condition_ --> [[Espressione|espressione]]
- _statement_ --> gruppo di [[Istruzione|istruzioni]]

<u>Attenzione</u>: può capitare che le condizioni risultino sempre vere, portando a cicli infiniti.

> Il **while** viene utilizzato per cicli di cui non si può determinare con precisione per quante volte saranno eseguiti.

#### Es.
Esempio in [[C++]]
```cpp
int main() {
	int conta = 10;
	while (conta > 0) {
		cout << "ciao" << endl;
		conta = conta - 1;
	}
	return 0;
}
```

#### Potenza
Con il `while` si ottiene il [[Potere espressivo|potere espressivo]] della [[Macchina di Turing|macchina di Turing]].

### Do-while
Fondamentalmente il `do-while` inverte i **due elementi fondanti dell'iterazione**: dal _guardia-corpo_ del `while-do` passa al _corpo-guardia_.

## Cicli annidati
Quando i cicli cominciano a diventare complessi, per esempio eseguiti _uno dentro l'altro_, risulta necessario _tenere maggiormente d'occhio le metodologie principali per controllarli_:
- **contatori**
- **flag**

Talvolta, come nel caso della [[Congettura di Collatz|congettura di Collatz]], risultano fondamentali controlli del genere per **non incorrere in cicli infiniti**.

## Referenze
