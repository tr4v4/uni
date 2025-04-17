---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 12-10-2023 19:13:07
links:
  - "[[Lecture 11102023092734]]"
  - "[[Lecture 12032025111631]]"
---
# Passaggio per riferimento
---
## Introduzione
> Nel **passaggio per riferimento** all'invocazione della [[Funzione informatica|funzione]] _viene preso l'indirizzo della locazione di [[RAM|memoria]] dell'[[Identificatore|identificatore]] passato per parametro_. Di conseguenza, le modifiche al parametro formale passano automaticamente all'attuale.

Questo **crea un legame** tra la variabile passata in ingresso e l'_alias_ utilizzato dalla funzione. Fondamentalmente **non passo il contenuto** (come avviene nel caso del [[Passaggio per valore|passaggio per valore]]), **passo il contenitore**.

Di fatto, questo meccanismo sfrutta l'[[Aliasing|aliasing]] a suo vantaggio.

### Benefici
Ci sono casi in cui il passaggio per valore non basta. Per esempio _se si vogliono returnare 2 valori_ l'unico modo alternativo sarebbe di utilizzare variabili globali. Ma, in generale, è meglio **evitare il più possibile l'utilizzo di variabili globali e di funzioni che lavorano su di esse**: il passaggio per riferimento è la soluzione più valida.

Un altro grande beneficio di questa modalita' di passaggio e' il fatto che sia piu' efficiente di quello per valore: non devo copiare il parametro attuale in quello formale (si pensi a [[Oggetto informatico|oggetti]] di grandi dimensione come in [[Java]]).

## Sintassi
I parametri formali devono essere dichiarati con l'operatore `&` (_ampersand_). Questo infatti, di una variabile ne restituisce l'indirizzo a cui fa riferimento in memoria.

<u>Nota bene</u>: questa modalità di scrittura è _molto discorsiva_. Se si nota che una funzione prende dei parametri per riferimento è bene rendersi conto che **potrebbe modificare le variabili del chiamante**.

### Esempio
```cpp
void switch(int &a, int &b) {
	int temp;
	temp = a;
	a = b;
	b = temp;
}

int main() {
	int a = 4, b = 5;
	switch(a, b);
}
```

## Referenze