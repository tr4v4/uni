---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 25-10-2023 14:23:47
links:
  - "[[Lecture 24102023100626]]"
  - "[[Lecture 22112023092107]]"
---
# Ricerca dicotomica
---
## Introduzione

### Versione iterativa
```cpp
int ricerca_dicotomica(int v[], int n, int s) {
	int i=0, j=n;
	bool found = false;
	while (!found && i<j) {
		int m = v[(i+j)/2];
		if (m == s) found = true;
		else if (m < s) i = (i+j)/2 + 1;
		else j = (i+j)/2;
	}
	return (i+j)/2;
}
```

### Versione [[Ricorsione|ricorsiva]]
```cpp
int ricerca_binaria(int v[], int n, int i, int j) {
  if (v[(i + j) / 2] == n)
    return (i + j) / 2;
  else if (i > j)
    return -1;
  else if (v[(i + j) / 2] > n)
    return ricerca_binaria(v, n, i, (i + j) / 2 - 1);
  else
    return ricerca_binaria(v, n, (i + j) / 2 + 1, j);
}
```
La funzione termina (_non diverge_) perché la chiamata ricorsiva avviene su una distanza tra gli indici sempre minore, fintanto che non si raggiunge uno dei due _casi base_:
- il numero è stato trovato;
- l'indice `i` ha superato l'indice `j` e quindi il numero non esiste nell'[[Array|array]].

<u>Nota bene</u>: affinché la funzione lavori su porzioni sempre più piccole dell'array occorre aumentare il numero dei parametri rispetto alla versione iterativa (i due indici).

## Referenze