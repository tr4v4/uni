---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 13:53:59
links:
  - "[[Lecture 26092024150810]]"
---
# Markup
---
## Introduzione
I dati non esistono in natura, richiede un intervento umano che identifica una quantità e attribuisce un valore, per scopi vari. I più complessi, sono organizzati in **[[Strutture dati|strutture dati]], che ne esplicitano il significato**. Il dato di per sé, infatti, non ha scopo ed è privo di utilizzabilità; se al dato si associa un'etichetta otteniamo una _coppia chiave-valore_ che diventa informazione; se inseriamo ogni coppia chiave-valore all'interno di una struttura chiamata _record_ diamo del contesto a quell'informazione, che diventa parte delle _proprietà_ di quell'entità.

Un record, per definizione, è una collezione di elementi di dati etichettati, che descrivono una singola entità.

Le strutture dati si dividono per tipologie:
- [[Lista|liste]]
- [[Tabella|tabelle]], liste di _record_
- [[Albero informatico|alberi]], per ovviare alla ridigità delle tabelle; offrono due forme di gerarchia
	- _dominio_, gerarchia di potere (come negli eserciti);
	- _contenimento_, gerarchia per gli elementi geometrici;
- [[Grafo|grafi]]

Poi c'è il **testo**, che  non è né un dato, né un record, né una struttura dati. Del testo si sa che:
- ha una _struttura_ (di contenimento, ossia blocchi di testo organizzati in modo gerarchico)
- ha un _ordine_ (alcune parti vengono prima di altre)
- ha parti _significative_ e importanti da identificare e altre che non lo sono

Allora la **teoria del markup** descrive i testi come un albero ordinato ed etichettato di elementi e nodi di testo. In particolare:
- la struttura è completamente descritta dall'albero, ma gli elementi all'interno della gerarchia sono in un ordine non ignorabile
- i nodi devono essere etichettati in modo esplicito
- il contenuto di ogni nodo è misto

### Formati
Ogni dato dovrà essere codificato in un certo formato, a seconda della struttura dati in cui è contenuto:
- tabelle
	- [[CSV]] - si risolve il problema dell'utilizzo della virgola o del cambio riga con l'_escaping_; scomodo per tabelle con tanti campi
	- Tab-delimited values
	- [[Excel]] - formato XLSX
- alberi
	- [[JSON]] - fantastico e tutto ma per la trasmissione di contenuto misto è poco potente
	- [[YAML]] - come JSON ma ispirato alla sintassi [[Python]]
- grafi
	- [[RDF]]
- testo
	- plain-text
	- markdown
	- [[HTML]] - attuale formato di punta per i documenti di testo sul [[Web|web]]
	- [[XML]] - a differenza di HTML, che ha un vocabolario predefinito, XML è una sintassi per definire dei vocabolari (meta-linguaggio di markup)

## Definizione
> Il **markup** è l'insieme di ogni mezzo per rendere esplicita una particolare interpretazione di un testo.

Quindi si tratta di _tutte quelle aggiunte al plain-text che permettono di renderlo più fruibile_. Per esempio la _punteggiatura_, il _margine per creare effetti su un testo_, non fanno parte del testo, ma del markup: _servono per dare un certo tono al testo, ad esplicitarne il significato_.

### Piramide
![[piramide-markup.png]]

### Modi
Ci sono tantissime modalità del markup:
- proprietario vs. pubblico
- binario vs. leggibile
- interno vs. esterno
- puntuazionale vs. presentazionale
- procedurale vs. descrittivo
- referenziale vs. metamatkup

## Linguaggi
I linguaggi del markup sono:
- [[TROFF]]/[[NROFF]] è il formatter su cui si basano i manuali di ogni comando [[Linux]] visualizzabili con `man`
- [[TeX]] e [[LaTeX]], realizzato (il primo) da [[Donald Knuth]], è [[Turing-completezza|Turing-completo]] (ossia è un linguaggio di programmazione vero e proprio!) molto complesso, consente di creare anche librerie --> una di queste è LaTeX, una libreria per i documenti scientifici
- [[SGML]], meta-linguaggio non proprietario di markup descrittivo

## Referenze