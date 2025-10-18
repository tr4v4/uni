---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 13:53:01
links:
  - "[[Lecture 26022025111603]]"
---
# Display
---
## Introduzione
> Il **display** e' una tecnica usata per rendere piu' efficiente l'implementazione della [[Scope statico|regola di scope statico]] rispetto alla [[Catena statica|catena statica]].

## Funzionamento
L'idea e' di avere un vettore di [[Puntatore|puntatori]], _in cui in ogni cella $i$ si trova il puntatore al [[Record di attivazione|record di attivazione]] di livello $i$ che e' stato creato piu' recentemente e che e' attualmente attivo_.

Per esempio, se si considera il programma
![[catena-statica-1.png]]

e la sequenza di chiamate `A, B, C, D, E, C`, allora il display si evolve nella seguente maniera:
1. viene chiamato `A` e all'interno di essa anche `B`; il display sara' ![[display-1.png]]
2. viene chiamato `C` da `B`, che si trova sul suo stesso livello, per cui il nuovo record di livello 2 attivo dovra' essere `C`, ma il link statico di `C` dovra' puntare a `B`; il display sara' ![[display-2.png]]
3. viene chiamato `D` da `C`, che si trova su un livello inferiore, per cui il nuovo record di livello 3 attivo dovra' essere `D`; il display sara' ![[display-3.png]]
4. viene chiamato `E` da `D`, che si trova sullo stesso livello, per cui il nuovo record di livello 3 attivo dovra' essere `E`, ma il link statico di `E` dovra' puntare a `D`; il display sara' ![[display-4.png]]
5. e cosi' via...

Ora, per sapere dove risolvere un nome esterno, e' sufficiente conoscere il suo livello di annidamento (informazione fornita dal [[Compilatore|compilatore]]), e andare a valutarlo nel record di attivazione puntatato da `display[livello]`.

<u>Nota bene</u>: in realta' _il compilatore non ti dice il livello preciso in cui si risolve il nome, ma di quanti livelli devi risalire per trovarlo_.

## Implementazione
E' il chiamato a maneggiare il display.

## Osservazione
Sono rari i livelli di annidamento con profondita' $> 3$, per questo non si usa il display perche' richiederebbe un costo maggiore per il mantenimento: in questi casi si preferisce la catena statica, perche' su livelli bassi rimane efficiente.

## Referenze