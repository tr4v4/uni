---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-09-2024 11:23:14
links:
  - "[[Lecture 17092024110611]]"
---
# Evoluzione dei linguaggi di programmazione
---
## Introduzione
I [[Linguaggio di programmazione|linguaggi di programmazione]] hanno subito un'evoluzione in efficienza, espressività e quindi complessità incredibile nel corso di poco più di 50 anni:
- **anni 40-50**, preistoria: linguaggio macchina e [[Assembly|assembly]]
- **anni 50-60**, primi linguaggio ad alto livello
	- _[[FORTRAN]]_ per calcolo numerico-scientifico, uso di notazione matematica in espressioni
	- _[[ALGOL]]_ come linguaggio universale, per esprimere algoritmi: indipendenza dalla macchina, vicinanza con la notazione matematica, call by name, funzioni ricorsive, type systems, strutture dati (anche dinamiche)
	- _[[LISP]]_ per l'intelligenza artificiale (List Processor): funzioni su una certa classe di espressioni simboliche, ordine superiore (proto-paradigma funzionale)
	- _[[COBOL]]_ per applicazioni commerciali (record, archivi)
	- _[[ALGOL 68]]_ linguaggio barocco, complessa progettazione ma contiene la nuova idea della struttura a blocchi
	- _[[SIMULA]]_ da ALGOL primo linguaggio con classi e oggetti (proto-paradigma orientato a oggetti)
- **anni 70**:
	- _PL/I_ è FORTRAN + COBOL, primo linguaggio multi-uso
	- _[[PASCAL]]_ evoluzione e semplificazione di ALGOL W, didattico fino agli anni 80 (poi rimpiazzato da C e Java), portabile grazie a codice intermedio
	- _[[C]]_ programmazione di sistema (Unix), notevole successo
	- _[[Prolog]]_ usa esplicitamente la logica come base di un linguaggio di programmazione (primo [[Linguaggio di programmazione logico|linguaggio logico]])
	- _[[SmallTalk]]_ primo vero [[Linguaggio di programmazione orientato a oggetti|linguaggio orientato a oggetti]]
	- _[[ML]]_ primo vero [[Linguaggio di programmazione funzionale|linguaggio funzionale]]
- **anni 80**:
	- _[[ADA]]_ primo linguaggio real-time concorrente, notevole successo
	- _[[Postscript]]_
	- _[[C++]]_
	- _[[Standard ML]]_
	- _[[CLP]]_ linguaggio logico con vincoli
- **anni 90** (nasce [[Web]]!):
	- _[[Java]]_ altamente portatile (elevata portabilità per JVM e ByteCode!), object-oriented, programmi spediti su rete
	- _[[PERL]]_ linguaggio per text-processing
	- _[[HTML]]_
	- _[[XML]]_
- **anni 2000**: service-oriented computing, paradigma che usa i servizi come unità di base di computazione per progettare applicazioni integrate di business
	- _[[WSDL]]_
	- _[[WS-BPEL]]_
	- _[[Jolie]]_ sviluppato a Bologna!

In poche parole il grande cambiamento è stato il seguente:
- anni 50-60: compilazione dei programmi per ottenere efficienza; connessione diretta fra hardware e linguaggi (integers, reals, goto); "programmers cheap, machines expensive -> keep the machine busy"
- oggi: compilazione di programmi costruiti in modo efficiente; connessione diretta fra software design e linguaggio (encapsulation, records, ereditarietà, dichiaratività); "programmers expensive, machine cheap -> keep the programmer busy"

## Referenze