---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 09-10-2023 18:06:42
links:
  - "[[Lecture 09102023151504]]"
  - "[[Lecture 10102023093258]]"
  - "[[Lecture 11102023092734]]"
---
# Funzione informatica
---
## Introduzione
> La **funzione** è un costrutto alla base della programmazione, che consente di eseguire porzioni di codice già scritti, _riutilizzando stesse istruzioni per casi differenti_[^2].

A differenza delle [[Funzione matematica|funzioni matematiche]], che anche senza input devono per forza restituire un output (si pensi alle funzioni costanti), queste possono funzionare:
- _senza argomenti di input e senza ritorno di output_
- _con parametri di input e senza output_
- _con input/output_

### Benefici
I benefici derivanti dall'utilizzo delle funzioni sono:
- evitare ripetizioni dello stesso codice
- programmazione "a blocchi" _disgiunti_[^1]

## Sintassi
La sintassi di una funzione dipende dal suo scopo:
- **function-definition** --> definisco la funzione
- **function-call** (o **void-function-call**) --> invoco la funzione

### Definizione
```cpp
function-definition ::= type identifier (formal-parameters) {
	declaration-part statement-part
}
```

### Invocazione
```cpp
function-call ::= identifier(actual-parameters)
void-function-call ::= identifier(actual-parameters);
```

### Firma
La funzione, all'inizio del programma, **si può anche definire senza implementare**: si chiama _firma_, e consiste solo nella scrittura del _tipo_, _nome_ e _parametri formali_.

```cpp
void stampa_somma(int a, int b);

int main() {
	stampa_somma(5, 10);
}

void stampa_somma(int a, int b) {
	cout << a+b << endl;
}
```

## Tipologie
### No input/output
Definite `void`. Posso lavorare eventualmente con le proprie [[Identificatore#Tipologie|variabili locali o con variabili globali]].

### Input no output
Anch'esse definite come `void`.
Da tenere in considerazione che l'_ordine di valutazione dei parametri di input è arbitrario_ (non ci importa, diventa rilevante solo nel momento in cui di sono funzioni che ritornano un valore che modifica variabili globali necessarie alla funzione invocata).

### Input/output
Compare il vincolo del `return`:
- bisogna garantire sempre che la funzione returnerà un valore del tipo specificato
- dopo il return le istruzioni non verranno mai eseguite --> fa tornare il controllo al chiamante

<u>Nota bene</u>: si sconsiglia altamente l'utilizzo di `return` dentro [[Iterazione|cicli]].

## Passaggio dei parametri
Proprio per la distinzione tra la funzione matematica e quella informatica, a quest'ultima (per le funzioni con input) _i parametri d'ingresso possono essere passati in 3 principali modalità_:
- **[[Passaggio per valore|per valore]]**
- **[[Passaggio per riferimento|per riferimento/indirizzo]]**
- **[[Passaggio per costante|per costante]]**

## Referenze
[^1]: vedi [[Approccio top-down|approccio top-down]]
[^2]: si differenzia dalle [[Macro|macro]] perché _parametrizzabile_