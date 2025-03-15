---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-02-2025 10:21:29
links:
  - "[[Lecture 19022025111150]]"
---
# Blocco
---
## Introduzione
> Un **blocco** e' una _regione testuale del programma_, delimitato da un _inizio_ e una _fine_, che puo' contenere _[[Dichiarazione|dichiarazioni]] locali a quella regione_ (nell'[[Ambiente|ambiente locale]]).

Un blocco puo' essere anonimo o associato a una procedura ([[Funzione informatica|funzione]]). Inoltre, i blocchi si possono annidare (unica sovrapposizione possibile), e in tal caso vale la seguente **regola di visibilita'**: _una dichiarazione locale ad un blocco è visibile in quel blocco e in tutti i blocchi annidati, a meno che in essi non avvenga una nuova dichiarazione dello stesso nome_ (in tal caso viene fatta una disattivazione).

## Vantaggi
L'utilizzo dei blocchi nei [[Linguaggio di programmazione|linguaggi di programmazione]] porta a numerosi vantaggi:
- gestiscono i [[Nome|nomi]] a livello globale;
- rendono più chiaro il codice;
- ognuno può scegliere il nome che vuole (si evita _namespace pollution_);
- ottimizzano l'occupazione di memoria;
- rendono possibile la [[Ricorsione|ricorsione]].

## Referenze