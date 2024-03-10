---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/logica-per-informatica
date: 06-11-2023 22:12:26
links:
  - "[[Lecture 02112023091408]]"
  - "[[Lecture 17112023102404]]"
  - "[[Lecture 22112023134305]]"
  - "[[Lecture 21112023093438]]"
  - "[[Lecture 22112023092107]]"
---
# Ricorsione
---
## Introduzione
> Una [[Funzione informatica|funzione]] ricorsiva è una funzione **definita in termini di se stessa**, che termina perché si richiama su un _[[Definizione di essere sottoinsieme|sottoinsieme]] stretto_ dei suoi parametri.

L'idea alla base della ricorsione sta nel motto _divide et impera_: suddivido un problema in sottoproblemi, che se non sono in grado di risolvere scompongo in altrettanti sottoproblemi, e così via, fino ad arrivare al **caso base**, che sono in grado di risolvere.

Con la ricorsione, l'_informatica si avvicina alla matematica e alla logica_[^1].

## Teoria
### Informatica vs. Matematica
Ciò che separa l'informatica dalla matematica è:
- l'_ordine di grandezza degli oggetti che vengono presi in considerazione_: se in matematica, infatti, ciò con cui si ha a che fare è definibile attraverso una descrizione infinita (come i numeri)[^3], in informatica **i dati sono per definizione finiti**. Un insieme di dati, per esempio, è per forza enumerabile: altrimenti non sarebbe possibile rappresentarli in [[RAM|memoria]][^4];
- la _definizione di funzione_: in matematica una [[Funzione matematica|funzione]] è di una [[Relazione|relazione]], ovvero un sottoinsieme del [[Prodotto cartesiano|prodotto cartesiano]] tra un _dominio_ e un _codominio_, quindi di fatto è un insieme. In informatica, invece, una funzione si definisce come una procedura di calcolo, un _programma che da un input ricava un output_.

Ciononostante, alcuni [[Tipi di dati|dati informatici]] sono di tipo **unbounded**, ovvero cui dimensione non è definita a priori ma può evolversi in _runtime_: è il caso delle [[Strutture dati dinamiche|strutture dati dinamiche]]. Di fatto [[Lista|liste]], [[Stringhe|stringhe]], [[Albero informatico|alberi]] sono tutti dati enumerabili (possiamo sapere quante liste sono coinvolte in un programma), ma cui grandezza non è definibile a priori da una [[Costante informatica|costante]], per esempio.

La caratteristica principale di questi dati è che _sono costruiti mediante ricorsione_: all'interno di un dato unbounded si ritrovano delle parti dello stesso tipo. Per esempio una lista è definita da una testa collegata a una sottolista, a sua volta composta da una testa e una sottolista, e così via...

La struttura ricorsiva dei dati è fondamentale per la definizione di funzioni che gestiscono dati _unbounded_: un dato non definito ricorsivamente ma comunque di grandezza dinamica, per essere processato _dovrebbe esistere un programma di grandezza arbitraria_.

Ad ogni modo, per processare un dato unbounded, una porzione di codice di un programma dev'essere eseguito ripetutamente, attraverso:
- [[Comandi iterativi|cicli]]
- ricorsione

## Implementazione
Nella pratica quello che avviene è che ad ogni chiamata di funzione viene creato un [[Record di attivazione|record di attivazione]] _impilato_ sullo [[Stack|stack]][^2]. Arrivato al caso base, la funzione non reinvoca, portando a un **pop a catena** di tutti i record di attivazione, fino a tornare alla prima invocazione.

## Composizione
Le funzioni ricorsive si devono comporre di:
- _casi induttivi_
- _casi base_

### Progettazione
Per progettare una funzione ricorsiva si devono seguire le fasi:
1. _verificare che non ci siano ricorsioni infinite_, ovvero che la funzione non diverga
2. _verificare che ogni caso di base ritorni il valore corretto_
3. _verificare che ogni caso induttivo con chiamata ricorsiva sia corretto_

Come caso di studio fare riferimento alla versione ricorsiva della [[Ricerca dicotomica#Versione Ricorsione ricorsiva|ricerca binaria]].

### Mutua ricorsione
Esistono anche funzioni dette _mutuamente ricorsive_, ovvero un `f(x)` e un `g(x)` che si richiamano a vicenda. Il problema di quale definizione delle due è da definire prima si risolve grazie alla _scrittura dei prototipi_.

## Osservazioni
> Il numero di parametri formali di una funzione ricorsiva aumenta tanti quanti cicli annidati servirebbero per implementarla iterativamente.

Prendiamo in esempio due funzioni:
- _Funzione che stampa $n$ asterischi_

```cpp
// Versione ricorsiva
void ric_n_asterischi(int n) {
	if (n != 0) {
		cout << "*";
		n_asterischi(n - 1);
	}
}

// Versione iterativa
void it_n_asterischi(int n) {
	for (int i=0; i<n; i++) {
		cout << "*";
	}
}
```

- _Funzione che stampa asterischi per un numero di volte pari alla somma dei quadrati dei primi $n$ numeri naturali_

```cpp
// Versione ricorsiva
void ric_n_squared_asterischi(int n, int e, int f) {
	if (f > 0) {
		cout << "*";
		ric_n_squared_asterischi(n, e, f - 1);
	} else {
	    if (e > 1)
		    ric_n_squared_asterischi(n, e - 1, n);
	    else {
		    if (n > 0)
			    ric_n_squared_asterischi(n - 1, n - 1, n - 1);
		    else
		        return;
	    }
	}
}

// Versione iterativa
void it_n_squared_asterischi(int n) {
	for (int i=0; i<n; i++) {
		for (int j=i; j<n; j++) {
			for (int z=i; z<n; z++) {
				cout << "*";
			}
		}
	}
}
```

Si nota come _il numero di parametri di entrambe le funzioni ricorsive siano lo stesso dei numeri di cicli delle versioni iterative_.

### Ricorsione vs. Iterazione
E' possibile implementare algoritmi iterativi con la ricorsione e viceversa. Ci sono in ambo i casi vantaggi e svantaggi, per esempio la versione ricorsiva:
- _è meno efficiente di quella iterativa_ (es. sequenza di Fibonacci)
- _usa più memoria di quella iterativa_ (stack)
- _è più elegante di quella iterativa_

## Rischi
Il rischio principale della ricorsione è l'eventuale _ricorsione infinita_, ovvero quando si dice che la funzione **diverge**.

## Referenze
- [[Ricorsione strutturale]]

[^1]: vero, già visto in [[Logica proposizionale|logica proposizionale]] e nella [[Semantica classica#Definizione|definizione di semantica classica]]
[^2]: fare riferimento all'[[Allocazione dinamica della memoria|allocazione dinamica della memoria]]
[^3]: si veda [[ZF]]
[^4]: e non solo: abbiamo studiato che [[Rappresentazione dell'informazione|non è possibile rappresentare tutti i numeri con il massimo grado di precisione]]: si veda la [[Codifica floating-point|codifica floating-point]]