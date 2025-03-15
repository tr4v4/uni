---
tags:
  - category/note
  - status/finished
  - topic/calcolo-delle-probabilità-e-statistica
date: 04-03-2025 11:10:24
links:
  - "[[Lecture 28022025132238]]"
---
# Diagramma ad albero
---
## Introduzione
> Il **diagramma ad albero** e' uno _strumento usato nello studio delle [[Probabilita'|probabilita']] (in particolare di quelle [[Probabilita' condizionata|condizionate]]) per visualizzare tutti i possibili [[Esito|esiti]] dell'[[Esperimento aleatorio|esperimento]]_. Si compone nel seguente modo:
> - ogni nodo e' un evento (la radice e' lo [[Spazio campionario|spazio campionario]] $\Omega$);
> - ogni ramo e' una probabilita' (i primi non condizionati, tutti gli altri condizionati);

## Caratteristiche
Il risultato della composizione comporta le seguenti conseguenze:
- i **rami che escono da un medesimo nodo conducono ad eventi tra loro disgiunti la cui unione e' $\Omega$** (la somma delle loro probabilita' e' 1);
- scelto un [[Cammino|cammino]] che collega la radice ad un evento, il prodotto delle probabilita' dei rami del cammino equivale alla probabilita' dell'intersezione degli eventi; in altre parole **vale la [[Regola della catena|regola della catena]] sui rami dell'albero**;

Quest'ultima proprieta' si riassume dicendo che i rami che escono da un medesimo nodo conducono ad una [[Partizione dello spazio campionario|partizione]] di $\Omega$.

## Referenze