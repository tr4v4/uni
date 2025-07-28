---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 04-05-2025 18:39:16
links:
  - "[[Lecture 04042025092728]]"
---
# LOOK
---
## Introduzione
> Il **LOOK**, anche detto **algoritmo dell'ascensore**, è un [[Algoritmo|algoritmo]] di [[Disk scheduling|disk scheduling]] tra i piu' efficaci.

## Funzionamento
Alla testina viene associato un verso: `salita` o `discesa`. Questa si sposta di richiesta in richiesta, mantenendo la direzione fino a che non trova l'ultima richiesta in quella direzione. A questo punto cambia direzione e continua a spostarsi fino a che non trova l'ultima richiesta in quella direzione. E cosi' via.

E' estremamente efficiente, ma sono privilegiate le tracce centrali.

## Problema
Insieme al [[C-LOOK]], l'algoritmo gemello, ha un problema: se ci sono molte richieste concentrate in una parte del disco, la testina potrebbe rimanere bloccata li', generando [[Starvation|starvation]] per le altre richieste.

Per sbloccare la situazione si usano due [[Coda|code]]:
- una per le richieste in salita;
- una per le richieste in discesa.

In questo modo, se si e' sul cilindro $x$ e arrivano ulteriori richieste per $x$ o superiore, queste verranno messe nella coda opposta a quella della direzione corrente, evitando cosi' la starvation.

## Referenze