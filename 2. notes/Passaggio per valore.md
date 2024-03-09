---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 12-10-2023 19:11:01
links:
  - "[[Lecture 11102023092734]]"
---
# Passaggio per valore
---
## Introduzione
>  All'invocazione della [[Funzione informatica|funzione]] _il valore dell'[[Espressione|espressione]] passato per parametro viene assegnato al parametro formale della funzione_.

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