---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 21-10-2024 20:50:31
links:
  - "[[Lecture 15102024110302]]"
---
# Lex
---
## Introduzione
> **Lex** è un software di [[Unix]] che _genera [[Analisi lessicale|analizzatori lessicali]]_ (o _scanner_).

Esiste anche FLEX, la versione più recente e aggiornata di Lex ma equivalente.

## Funzionamento
Lex funzione nel seguente modo:
- prende in _input_ un file `.l` contenente _un insieme di definizioni regolari e una serie di azioni corrispondenti_;
- restituisce in _output_ un file in [[C]] `.c` che _realizza l'automa riconoscitore e che associa ad ogni istanza di una definizione la relativa azione_ (solitamente agire sulla lista di token).

![[diagramma-lex.png]]
![[diagramma-lex-2.png]]
![[diagramma-lex-3.png]]

## Input
Il file preso in input `lex.l` si suddivide in 3 parti:
1. **dichiarazioni**, [[Espressione regolare|espressioni regolari]] per ogni categoria sintattica;
2. **regole**, associazioni tra espressioni regolari (pattern) e azioni (scritte in C, solitamente la stampa del token);
3. **funzioni ausiliarie**, da definire se si richiamano funzioni complesse nella parte di "azione" delle regole.

## Output
Lo scanner `lex.yy.c` restituito in output da Lex è il programma che **implementa un unico [[DFA]] che riconosce tutti i pattern**.

In particolare:
1. scandisce il testo sorgente in cerca di lessemi di pattern;
2. quando riconosce un lessema esegue l'azione specificata;
3. quando l'input non corrisponde a nessun pattern, lo lascia inalterato e segnala la cosa al gestore degli errori.

### Funzionamento
Nel dettaglio vengono generati dei singoli [[NFA]] per ogni pattern, uniti da uno stato iniziale con delle transizioni-$\epsilon$. A questo punto viene **simulato un DFA che contemporaneamente agisce su tutti i pattern**, _implementando in real-time l'[[Costruzione per sottoinsiemi|algoritmo di costruzione per sottoinsiemi]]_.

Il DFA simulato deve garantire due importantissimi aspetti finora mai visti:
- _se dei pattern condividono lo stesso prefisso viene cercato sempre il lessema più lungo_;
- _se vengono riconosciuti più pattern per uno stesso lessema viene identificato sempre il pattern dichiarato prima_;

<u>Nota bene</u>: quindi l'ordine di scrittura delle regole nel file `lex.l` è importante!

Per garantire questi due meccanismi il DFA simulato procede nel seguente modo:
1. va avanti a leggere l'input finché non si blocca, spostandosi contemporaneamente sugli stati di tutti i singoli NFA per pattern;
2. quando si blocca guarda lo stato in cui si trova:
	- _se è di riconoscimento_ --> ha trovato il match con il pattern;
	- _se non è di riconoscimento_ --> risale la successione di transizione di stati fino a trovarne uno di riconoscimento, e quello sarà il pattern scelto;
		- _questo garantisce proprio che se più pattern condividono uno stesso prefisso venga scelto il più lungo_
3. se arrivati al match più di uno (sotto-)stato del DFA simulato è finale (di riconoscimento), allora scelgo il pattern elencato prima;
	- _questo garantisce che se vengono riconosciuti più pattern per uno stesso lessema viene identificato sempre il pattern dichiarato prima_
4. trovato il match corretto, elimina la sottostringa dell'input matchata e riparte da capo con la parte rimanente;

E' per questo motivo che in `lex.l` le parole riservate del linguaggio (come `while`, `if`, ecc...) vanno messe prima degli identificatori. In questo modo:
- se si scrive una parola riservata questa viene riconosciuta come tale (è scritto prima!);
- se si scrive un identificatore che contiene la parola riservata questo viene riconosciuto come tale (prefisso più lungo!);

## Utilizzo con YACC
In realtà l'analisi lessicale viene fatta in parallelo con l'[[Analisi sintattica|analisi sintattica]]. Preso [[YACC]] che produce l'analizzatore sintattico (come Lex con il lessicale), **il programma prodotto da Lex funge da subroutine del parser**. Si dice che `lex.yy.c` è usato _on-demand_ dall'analizzatore sintattico, che _richiede di volta in volta il token successivo_.

![[lex-yacc.png]]

Esistono di fatto alcune variabili comuni tra Lex e YACC, come `yylval`, che permettono ai due di scambiarsi informazioni, come il token riconosciuto. In particolare `yylex()` restituisce il nome del token cui valore è salvato in `yylval`.

## Referenze