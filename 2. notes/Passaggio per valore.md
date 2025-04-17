---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 12-10-2023 19:11:01
links:
  - "[[Lecture 11102023092734]]"
  - "[[Lecture 12032025111631]]"
---
# Passaggio per valore
---
## Introduzione
>  Nel **passaggio per valore** all'invocazione della [[Funzione informatica|funzione]] _il valore dell'[[Espressione|espressione]] passato per parametro viene assegnato al parametro formale della funzione_, che si comporta come una variabile locale.

### Esempio
```cpp

void stampa_somma(int a, int b) {
	cout << a+b << endl;
}

int main() {
	int a = 1;
	stampa_somma(5+4, a+3);
}

```

## Referenze