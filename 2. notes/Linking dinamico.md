---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 19:16:14
links:
  - "[[Lecture 22112023151203]]"
---
# Linking dinamico
---
## Introduzione
A differenza di quanto avviene con il [[Linking statico|linking statico]], ci possono essere casi in cui i moduli oggetto non vengono uniti in [[Workflow di compilazione|fase di compilazione]], ma _linkati_ al momento dell'esecuzione del programma stesso (in _runtime_): questo è il **linking dinamico**.

## Implementazione
Un metodo di implementazione del linking dinamico è attraverso l'utilizzo di un [[Segmentazione|segmento]] che contiene nomi e indirizzi delle librerie, _inizializzati appositamente a indirizzi sbagliati_. Il programma viene appositamente modificato così da contenere, per ogni chiamata di funzione, il collegamento alla rispettiva porzione di quel segmento riservata alla libreria. Così, quando un programma richiama una funzione di libreria, il [[Sistema operativo|sistema operativo]] la ricerca in tale segmento, trovando un indirizzo sbagliato che genera una [[Trap|trap]]: il gestore della medesima cerca la libreria, la carica in memoria e scrive il giusto indirizzo nel segmento, così che le future chiamate non generino più trap.

Questa implementazione "a trap" consente di non dover avere sempre in memoria tutte le librerie installate, ma solo quelle di volta in volta invocate.

## Vantaggi
Questo _velocizza molto il processo di compilazione nel caso in cui la procedura di un modulo esterno venga invocata rare volte_: non avrebbe senso creare, con tutto ciò che esso comporta, un unico modulo per invocazioni sporadiche.

## Utilizzi
Questo sistema viene usato nei [[DLL]] di [[Windows]]: sarebbe inutile inserire, in tutti gli eseguibili, le stesse librerie; inoltre, in caso di aggiornamento, bisognerebbe ricompilare tutti gli eseguibili che includono tali librerie.

## Referenze