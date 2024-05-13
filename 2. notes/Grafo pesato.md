---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 28-04-2024 23:37:23
links:
  - "[[Lecture 24042024111954]]"
---
# Grafo pesato
---
## Introduzione
> Un **[[Grafo|grafo]] pesato** è un _grafo cui archi sono pesati_, ovvero a cui è associato un peso (o costo), solitamente un [[Numeri reali|reale]]. Il costo può essere determinato tramite una [[Funzione matematica|funzione]] di costo $c: E \to \mathbb{R}$, e quando tra due vertici l'arco non esiste viene associato un costo infinito $\infty$.

### Applicazioni
Una [[Matrice di adiacenza|matrice di adiacenza]] sarebbe composta da costi reali per ogni arco connesso, e da costi infiniti per ogni arco non connesso. L'equazione diverrebbe
$$M(u, v) = \begin{cases}c(u, v) & \{u, v\} \in E \\ \infty & \{u, v\} \notin E \end{cases}$$

## Referenze