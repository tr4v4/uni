---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 09-10-2023 17:50:42
links:
  - "[[Lecture 09102023151504]]"
  - "[[Lecture 10102023093258]]"
---
# Scope
---
## Introduzione
> La **portata di una [[Dichiarazione|dichiarazione]]**, anche detta **scope** definisce per quale _blocco_ di codice vale un certo [[Identificatore|identificatore]].

In generale si dice che una dichiarazione vale solo e solamente per il blocco a cui appartiene: al di fuori di esso l'identificatore non è raggiungibile[^1].

Per esempio, considerando il seguente blocco di codice
```cpp
int x = 1;
{ int y = 2; }
cout << x << y;
```
questo genererebbe errore perché dopo l'esecuzione del blocco `{ int y = 2; }`, l'identificatore `y` non esiste più in [[RAM|memoria]].

<u>Osservazione</u>: in un blocco è possibile dichiarare nuovi identificatori, o addirittura _ridichiararne di vecchi_!

## Casistiche
Nel caso delle [[Funzione informatica|funzioni]] bisogna agire allo stesso modo: considerare per ogni blocco l'identificatore che si trova più vicino. Se il riferimento è dentro il proprio blocco allora verrà preso in considerazione quello; altrimenti il blocco "cercherà" l'identificatore al di fuori, arrivando eventualmente alle _variabili globali_.

Es.
```cpp
int m;
int n;
void min() {
	int tmp;
	if (m > n) {tmp = m; m = n; n = tmp;}
}
int main() {
	cin >> m >> n;
	{
		int m = 7;
		min();
		cout << m << n;
	}
	return 0;
}
```
Il risultato di questo codice è `710`. Questo perché `min()` non vede la variabile locale del blocco di `main`, quindi per le regole della portata dei dati va a prendere il valore di `m` e `n` subito fuori dal suo blocco.

## Referenze
[^1]: funziona un po' come le regole grammaticali: dopo il punto il soggetto perde la sua valenza per la frase successiva