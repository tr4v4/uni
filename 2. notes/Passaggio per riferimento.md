---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 12-10-2023 19:13:07
links:
  - "[[Lecture 11102023092734]]"
---
# Passaggio per riferimento
---
## Introduzione
> All'invocazione della [[Funzione informatica|funzione]] _viene preso l'indirizzo della locazione di [[RAM|memoria]] dell'[[Identificatore|identificatore]] passato per parametro_.

Questo **crea un legame** tra la variabile passata in ingresso e l'_alias_ utilizzato dalla funzione. Fondamentalmente **non passo il contenuto** (come avviene nel caso del [[Passaggio per valore|passaggio per valore]]), **passo il contenitore**.

### Benefici
Ci sono casi in cui il passaggio per valore non basta. Per esempio _se si vogliono returnare 2 valori_ l'unico modo alternativo sarebbe di utilizzare variabili globali. Ma, in generale, è meglio **evitare il più possibile l'utilizzo di variabili globali e di funzioni che lavorano su di esse**: il passaggio per riferimento è la soluzione più valida.

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