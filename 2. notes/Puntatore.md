---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 05-11-2023 16:36:00
links:
  - "[[Lecture 03112023110813]]"
  - "[[Lecture 07112023104204]]"
  - "[[Lecture 08112023095400]]"
---
# Puntatore
---
## Definizione
> I **puntatori** sono il [[Tipi di dato|tipo di dati]] degli indirizzi di memoria.

Il puntatore è un _concetto complesso_ perché non ha un'_equivalenza matematica_[^1]: non esiste alcun contenitore in matematica, è un qualcosa che ha senso solo per l'informatica.

I puntatori sono, inoltre, un _tipo di dato parametrico_, ovvero cui grandezza dipende dal tipo di elemento a cui punta. In breve **non esiste il tipo di dato puntatore**[^5], esiste il puntatore a un intero, il puntatore a un double, ecc...

## Sintassi
Per dichiarare un puntatore è possibile utilizzare `*`, come:
```cpp
int *p;
char *c;
...
```

## Operazioni
Con i puntatori è possibile svolgere 4 principali operazioni:
- _allocazione_ --> `new`
- _cancellazione_ --> `delete`
- _annullamento_ --> `NULL`
- _dereferenziazione_ --> `*`
- "_indirizzo di_" --> `&`

Le uniche altre operazioni attuabili sui puntatori sono $==$ e $!=$: non ha senso un confronto di maggioranza o minoranza su indirizzi di memoria (quindi $>=$ e $<=$).

### Allocazione
Nel momento in cui si inizializza un puntatore con il costrutto `new`, viene **allocata dinamicamente** nell'[[Heap|heap]][^2] una porzione di memoria che sarà la cella a cui punta il puntatore.

Per esempio, il codice
```cpp
int *p = new int;
```

alloca nell'_heap_ (quindi in _runtime_) una porzione di memoria riservata a un _intero_, a cui punterà il puntatore `p`.

<u>Attenzione</u>: un ciclo infinito di allocazione in heap potrebbe portare al _riempimento della memoria_[^4].

### Cancellazione
Se un puntatore è stato inizializzato con un'allocazione in _heap_ (`new`), allora questo può anche essere cancellato attraverso l'operazione `delete`. Quello che avviene nel dettaglio è che il _puntatore continua a puntare alla locazione in memoria_, ma quest'ultima **viene contrassegnata come sovrascrivibile**.

Per questo motivo se non si pone, subito dopo la cancellazione, il puntatore a `NULL`, si rischia (a seconda del [[Compilatore|compilatore]]) di incorrere in un **dangling pointer**: un _puntatore che punta a un'area non stabile della memoria_.

_Deferenziare un dangling pointer_, a questo punto, diventa una _mossa estremamente pericolosa_: si rischiano di sovrascrivere altri dati assegnati a nuovi puntatori.

<u>Nota</u>: è con questo principio che vengono "eliminati" i file nelle [[Memorie#Classificazione|memorie persistenti]], ovvero di fatto i puntatori rimangono ma le locazioni a cui puntano diventano sovrascrivibili.

### Annullamento
L'operazione di annullamento permette di assegnare `NULL` a un qualunque puntatore (a prescindere dal tipo). `NULL` è una [[Costante informatica|costante]], supportata da diverse [[Libreria|librerie]] tra cui `iostream`[^3].

### Dereferenziazione
E' l'operazione più utilizzata dopo l'_allocazione_, e consente di accedere alla cella a cui punta un puntatore.

Per esempio:
```cpp
int *p;
*p = 5;
cout << *p;
```
stampa `5`.

### "Indirizzo di"
L'operatore `&` posto prima di una variabile restituisce il suo indirizzo in [[RAM]], _cui valore può essere inserito in un puntatore_.

Si tratta di un operatore applicabile a qualunque _[[Lhs-expression|lhs-expression]]_, per cui a:
- [[Identificatore|variabili]]
- [[Array|array]] (e i suoi elementi)
- [[Struttura dati|strutture dati]] (e i suoi campi)
- puntatori stessi

Per esempio, il codice
```cpp
int *p;
int n = 5;
p = &n;
```
inserisce nel puntatore `p` l'indirizzo della cella `n`.

<u>Attenzione</u>: si produce un _side effect_, quello ovvero di legare il contenuto di `n` con il contenuto della cella a cui punta `p`. Fare attenzione insomma al fatto che _quando si modifica `*p`, si modifica anche `n`_.

## Utilizzi
### Aliasing
Fare attenzione all'**aliasing**, ovvero a quando _due puntatori puntano alla stessa cella_: se si modifica la locazione a cui punta uno dei puntatori, si modifica la stessa a cui punta l'altro.

### Passaggio a funzioni
I puntatori possono essere passati come argomenti di [[Funzione informatica|funzioni]], o meglio, _alle funzioni si possono passare indirizzi di locazioni di memoria che saranno assegnati a puntatori interni alle funzioni_. Non per niente i puntatori sono _mascheratamente_ utilizzati per il [[Passaggio per riferimento|passaggio per riferimento]].

La sintassi è la seguente:
```cpp
void divide(int dvd, int dvs, int *q, int *r);

int main() {
	int risultato, resto;
	divide(10, 3, &risultato, &resto);
}
```

### Errori comuni
- **mai ritornare puntatori a variabili locali delle funzioni** --> le variabili locali non esistono più una volta che è terminata l'esecuzione della funzione (siamo nello [[Stack|stack]][^2]), perciò verrebbe ritornato un puntatore a una cella di memoria che è considerata come sovrascrivibile: _dangling pointer_
- **fare attenzione ai puntatori non inizializzati** --> viene generato un _Null-pointer Exception_

## Referenze
[^1]: un altro esempio di differenza tra informatica e matematica
[^2]: si veda l'[[Allocazione dinamica della memoria dei programmi|allocazione dinamica della memoria]]
[^3]: libreria standard di [[C++]]
[^4]: errore scatenato da una [[Trap|trap]]!
[^5]: anche se attraverso la [[Definizione di tipi di dati|definizione di tipi di dati]] ci si può semplificare la vita