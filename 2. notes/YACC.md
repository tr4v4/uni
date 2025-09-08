---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 08-09-2025 17:21:51
links:
---
# YACC
---
## Introduzione
> **YACC** (**Yet Another Compiler-Compiler**) e' un software che genera [[Analisi sintattica|analizzatori sintattici]].

## Funzionamento
Il software YACC funziona nelle seguente fasi:
- prende in input un file `.y` che specifica la [[Grammatiche libere|grammatica libera]] del linguaggio di cui si vuole fare [[Parser|parsing]];
- in output fornisce un file `.tab.c` che realizza il [[Parser LALR|parser]] $LALR(1)$[^1];
- il parser viene compilato;
- in input al parser e' fornita la lista di token prodotta dall'[[Analisi lessicale|analizzatore lessicale]] (tipo [[Lex]]);
- in output il parser restituisce l'[[Albero di derivazione|albero di derivazione]] dalla lista di token.

![[yacc.png]]

### Realta'
Nella realta' dei fatti la comunicazione tra [[Scanner|scanner]] e parser non e' definita in questo modo: **l'analizzatore sintattico usa l'analizzatore lessicale come subroutine**.
![[lex-yacc.png]]

In particolare il parser invoca lo scanner _on-demand_, richiedendo di volta in volta il token successivo. Le informazioni sono scambiate attraverso:
- `yyval` - una variabile comune ai due programmi che contiene il _puntatore nella [[Tabella dei simboli|tabella dei simboli]] al lessema appena individuato_;
- `yylex()` - una funzione invocata dal parser per richiedere allo scanner il token successivo;

## Input
La struttura di un file yacc (`.y`) e' la seguente:
- **prologo** - opzionale, contiene definizioni di macro e altre dichiarazioni di variabili o funzioni usate nelle sezioni successive;
- **definizioni** - dichiarazioni di simboli usati nella descrizione della grammatica (nomi dei token, condivisi con Lex); e' anche possibile in questa sezione definire la precedenza e l'associativita' degli operatori (terminali);
- **regole**;
- **funzioni ausiliarie** - contiene le funzioni di supporto per la generazione del parser; come `yylex()` (nel caso in cui non sia usato Lex, altrimenti bisogna includerlo con `#include "lex.yy.c"`).

### Regole
Le regole sono le dichiarazioni della grammatica libera del linguaggio. Sono scritte nella forma:
```y
nonterm: corpo1    {azione semantica 1}
		 corpo2    {azione semantica 2}
		 ...
		 ;
```
dove `{azione semantica i}` contiene il _codice [[C]] da eseguire nel momento in cui il parser riduce mediante quella produzione_.

Un carattere tra singoli apici ('a') e' un terminale. Il _simbolo iniziale della grammatica e' il nonterminale usato nella prima regola_.

#### Azione semantica
Nel dettaglio, l'_azione semantica deve calcolare il **valore semantico** della testa della produzione in funzione dei valori semantici dei simboli che compongono il corpo_.

Infatti YACC non e' solo usato per i compilatori, ma _anche come interprete_! Nel dettaglio il **valore semantico** potrebbe essere:
- l'_albero di derivazione_ - nel caso di compilatori;
- il _codice intermedio_ - se andiamo direttamente a produrre codice intermedio;
- la _valutazione dell'espressione_ - nel caso in cui **stiamo producendo un interprete**!

In un'azione semantica
- `$$` si riferisce al valore semantico della testa della produzione;
- `$i` si riferisce al valore semantico dell'i-esimo simbolo nel corpo della produzione.

![[yacc-regole-esempio.png]]

## Output
La [[Tabella di parsing LALR(1)|tabella di parsing]] $LALR(1)$ che genera YACC, poiche' la grammatica di base e' [[Grammatica ambigua|ambigua]], potrebbe contenere dei conflitti.
Ma usando le informazioni sull'**associativita'** e sulla **precedenza degli operatori** e' possibile risolverli tutti.

In generale, YACC quindi risolve i conflitti usando queste informazioni, e in assenza di indicazioni invece risolve:
- _conflitti shift-reduce_ - a favore dello shift;
- _conflitti reduce-reduce_ - a favore della produzione elencata prima;

<u>Nota bene</u>: e' anche possibile invcare YACC con il tag `-v`, che genera un file aggiuntivo `y.output` che contiene i nuclei degli insiemi di item trovati per la grammatica, una descrizione dei conflitti generati dall'algoritmo LALR e anche una rappresentazione leggibile della tabella di parsing che mostra come i conflitti sono stati risolti.

## Referenze

[^1]: ricordiamo che ogni linguaggio libero deterministico e' generabile da una grammatica $LR(1)$, e quindi _se possibile_ anche $LALR(1)$
