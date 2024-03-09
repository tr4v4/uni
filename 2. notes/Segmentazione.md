---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 16:55:47
links:
  - "[[Lecture 20112023130829]]"
---
# Segmentazione
---
## Introduzione
> La **segmentazione** è un _meccanismo di partizionamento logico della [[RAM|memoria]] di un calcolatore_.

## Principio di funzionamento
La memoria viene logicamente suddivisa in _segmenti logici_, ognuno di grandezza differente, adatta al suo scopo. Questi vengono virtualizzati, _slegati dalla loro implementazione fisica_, e **appaiono così a un generico programma come singole memorie distinte**.
![[segmentazione.png|500]]

Non si accede più, in poche parole, a un'unica grande memoria RAM, ma a singole porzioni identificate da un codice: nell'esempio sopra riportato, per accedere alla cella 24 del segmento dell'albero sintattico l'indirizzo dovrà essere composta da una _tupla_ `(3, 24)`, dove `3` è il numero del segmento, e `24` l'indirizzo all'interno del segmento.

<u>Nota bene</u>: gli indirizzi di ogni segmento, ovviamente, partiranno da 0. Ci sarà bisogno di un traduttore che converta gli indirizzi dei segmenti in indirizzi fisici.

## Implementazione
Come avviene per la [[Paginazione|paginazione]], _non tutti i segmenti possono stare in memoria_. Secondo lo stesso principio implementativo degli [[Algoritmi di paginazione|algoritmi di paginazione]], i segmenti vanno **swappati** tra memoria principale e secondaria.

Ma, a differenza di quanto avviene per lo scambio di pagine, cui grandezza è uguale a quella dei blocchi, _ogni segmento ha grandezza diversa_. Questo provoca il problema della [[Frammentazione esterna|frammentazione esterna]].

## Referenze
- [[Combinazione segmentazione-paginazione]]