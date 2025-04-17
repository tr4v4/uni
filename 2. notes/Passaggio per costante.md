---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 12-10-2023 19:33:26
links:
  - "[[Lecture 11102023092734]]"
  - "[[Lecture 12032025111631]]"
---
# Passaggio per costante
---
## Introduzione
> Nel **passaggio per costante** all'invocazione della [[Funzione informatica|funzione]] _i parametri formali vengono presi come costanti_, anche se passati come variabili. All'interno della funzione, perciò, **il loro valore è immutabile**.

### Esempio
```cpp
int calcola_distanza(const int a, const int b) {
	return abs(a - b);
}

int main() {
	int x = 10, y = 5;
	int distanza = calcola_distanza(x, y);
}
```

## Referenze