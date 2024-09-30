---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 29-09-2024 12:41:49
links:
  - "[[Lecture 23092024132935]]"
---
# Algoritmo iterativo
---
## Introduzione
> Un **algoritmo iterativo** è un [[Algoritmo|algoritmo]] che _approssima la soluzione di un problema matematico_ nel seguente modo: assegnato un valore iniziale $x_{0}$, si costruisce una [[Successione numerica|successione]] di valori $x_{0}, x_{1}, x_{2}, \cdots, x_{k}, x_{k+1}, \cdots$ tale che $x_{k} = g(x_{k-1})$ (dove $g$ è una [[Funzione matematica|funzione]]) con la proprietà
> $$x_{k} \longrightarrow_{k \to +\infty} x^{*}$$
> dove $x^{*}$ è la soluzione del problema.

Si tratta quindi di un _procedimento infinito_, che in quanto algoritmo, per definizione, dovrà essere troncato a un procedimento finito: questo genererà un [[Errore di troncamento|errore di troncamento]].

## Criteri di arresto
Il problema di algoritmi di questo tipo si concretizza nella domanda: **quando mi fermo?** L'idea è di stabilire un giusto _trade-off tra accuratezza e tempo di calcolo_, usandoli entrambi come criteri di arresto:
- **accuratezza** --> l'algoritmo viene interrotto quando viene _soddisfatto un certo grado di precisione della soluzione_;
- **tempo di calcolo**: l'algoritmo viene interrotto quando viene _superato un certo numero di iterazioni_.

Nella pratica questo si implementa con una doppia condizione sul `while` dell'algoritmo.

## Referenze