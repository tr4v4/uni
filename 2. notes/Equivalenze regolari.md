---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-10-2024 16:03:49
links:
  - "[[Lecture 10102024120505]]"
  - "[[Lecture 15102024110302]]"
---
# Equivalenze regolari
---
## Introduzione
> Le [[Espressione regolare|espressioni regolari]], gli [[NFA]], i [[DFA]] e le [[Grammatiche regolari|grammatiche regolari]] sono _tutti formalismi equivalenti_. Rispettivamente questi _denotano/riconoscono/generano_ i [[Linguaggio regolare|linguaggi regolari]].

![[Equivalenze regolari.canvas|Equivalenze regolari]]

Si noti che questo è possibile per via di 5 teoremi affrontati in precedenza:
- [[Equivalenza tra NFA ed espressioni regolari]]
- [[Costruzione per sottoinsiemi#Teorema]]
- [[Equivalenza tra DFA e grammatiche regolari]] (ed [[Equivalenza tra NFA e grammatiche regolari]])
- [[Grammatiche regolari#Teorema]]

## Passaggi
Di solito quello che si fa è:
1. definire un'espressione regolare;
2. costruire l'NFA associato;
3. ricavare il DFA equivalente;
4. [[Minimizzazione di DFA|minimizzare il DFA]];
5. ricavare la grammatica regolare del DFA minimo;
6. semplificare la grammatica (rimuovendo i simboli inutili);
7. ricavare dalla grammatica semplificata l'espressione regolare associata.

Ciò che si dovrebbe ottenere alla fine è un'espressione regolare $s'$ equivalente a quella originale $s$:
$$s' \simeq s$$

Questo è sufficiente per dire che **il diagramma delle equivalenze regolari commuta**.

## Referenze