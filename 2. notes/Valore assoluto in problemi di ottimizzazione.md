---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 17:46:33
links:
  - "[[Lecture 03032025091200]]"
---
# Valore assoluto in problemi di ottimizzazione
---
## Introduzione
### Vincoli
ll vincolo $|g(x)| \leq b$ si puo' facilmente esprimere nei due vincoli
$$g(x) \leq b \ \ \ \ \ -g(x) \leq b$$
assumendo che $b$ [[Numeri reali|reale]] positivo.

Tuttavia, in casi più complessi non è sempre possibile sbarazzarsi del [[Valore assoluto|valore assoluto]].

### Funzione obiettivo
Se la funzione obiettivo da massimizzare e' $|f(x)|$ con $x \in X$, allora si risolve risolvendo i due seguenti sottoproblemi
$$\max\{f(x) | x \in X\} \ \ \ \ \ \max\{-f(x) | x \in X\}$$
e confrontando i rispettivi valori ottimi (prendendo il massimo tra i due).

## Referenze