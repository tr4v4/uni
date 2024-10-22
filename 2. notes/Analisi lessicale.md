---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 20:14:55
links:
  - "[[Lecture 26092024120454]]"
  - "[[Lecture 03102024120247]]"
---
# Analisi lessicale
---
## Introduzione
> L'**analisi lessicale** è la prima fase attuata dal [[Compilatore|compilatore]], e consiste nella generazione della [[Tabella dei simboli|tabella dei simboli]] e della lista di _token_. In particolare un analizzatore lessicale, anche detto **scanner**, _riconosce nel programma in ingresso gruppi/sequenze di simboli che corrispondono a specifiche categorie sintattiche_ (come gli identificatori, parole riservate, operatori aritmetici, ecc...).

In particolare:
- spezza il codice sorgente in componenti sintattici primitivi (token)
- controlla che il lessico sia ammissibile
- riempie parzialmente la tabella dei simboli

Per la realizzazione si ha bisogno di:
- _[[Grammatiche regolari|grammatiche regolari]]_
- _[[Espressione regolare|espressioni regolari]]_
- _[[Linguaggio regolare|linguaggi regolari]]_
- _[[Automa a stati finiti|automi a stati finiti]]_

## Token
Un token è costituito da una coppia (_nome_, _valore_), dove:
- _nome_ è un simbolo astratto che rappresenta una categoria sintattica;
- _valore_ è una sequenza di simboli del testo in ingresso;

Per esempio, un token potrebbe essere `<Ide, x1>`: infatti `Ide` è il nome, ossia la categoria sintattica di `x1`, che è invece il valore della categoria sintattica.

Sui token ci possono poi essere:
- **pattern** - una descrizione generale della forma dei valori di una classe di token, un insieme dei valori ammissibili;
- **lessemi** - stringhe istanze di un pattern;

Per esempio `x1` è un lessema istanza del pattern $(x|y)(x|y|0|1)$.

<u>Nota bene</u>: in realtà, ogni token contiene la coppia (_nome_, _puntatore al valore_), dove il [[Puntatori|puntatore]] al valore sarà l'indirizzo del lessema nella tabella dei simboli.

L'idea è che _ad ogni categoria sintattica è associato un pattern_.

## Referenze