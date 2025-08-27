---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/linguaggi-di-programmazione
date: 16-09-2024 10:40:19
---
# Linguaggi di programmazione
---
## Lezioni
### Ultima lezione
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/linguaggi-di-programmazione SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/linguaggi-di-programmazione SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[1. lectures/Lecture 24102024120228.md\|Lecture 24102024120228]] | <ul><li>[[2. notes/Linguaggio libero deterministico.md\|Linguaggio libero deterministico]]</li><li>[[2. notes/Look-ahead.md\|Look-ahead]]</li><li>[[2. notes/Parser bottom-up.md\|Parser bottom-up]]</li><li>[[2. notes/Parser.md\|Parser]]</li><li>[[2. notes/Parser top-down.md\|Parser top-down]]</li><li>[[0. mocs/Linguaggi di programmazione.md\|Linguaggi di programmazione]]</li></ul> |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/linguaggi-di-programmazione AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/linguaggi-di-programmazione AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[1. lectures/Lecture 30042025110449.md\|Lecture 30042025110449]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 24042025131115.md\|Lecture 24042025131115]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 23042025111218.md\|Lecture 23042025111218]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 21112024121059.md\|Lecture 21112024121059]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 16042025110927.md\|Lecture 16042025110927]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 14052025105842.md\|Lecture 14052025105842]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 10042025131105.md\|Lecture 10042025131105]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 09042025110710.md\|Lecture 09042025110710]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 08052025131742.md\|Lecture 08052025131742]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 07052025110754.md\|Lecture 07052025110754]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->


## Note
- Argomenti
	- mod. 1
		- [[Linguaggio di programmazione]] (evoluzione, categorie, confronti)
		- [[Macchina astratta|Macchine astratte]], [[Linguaggio macchina]], [[Interprete]], [[Compilatore]]
		- [[Descrivere un linguaggio di programmazione]], [[Sintassi]], [[Semantica]], [[Pragmatica]], [[Implementazione]], [[Linguaggio formale]], [[Rappresentazione finita di un linguaggio]]
		- [[Grammatiche]], [[Derivazione]], [[Linguaggio generato]], [[Albero di derivazione]], [[Grammatica ambigua]]
		- [[Semantica statica]], [[Semantica dinamica]]
		- [[Struttura di un compilatore]]
		- [[Semantica operazionale strutturata]]
		- [[Espressione regolare]], [[Linguaggio denotato da un'espressione regolare]], [[Linguaggio regolare]], [[Automa a stati finiti]] ([[NFA]], [[DFA]], [[Costruzione per sottoinsiemi]]), [[Grammatiche regolari]], [[Equivalenze regolari]], [[Minimizzazione di DFA]] ([[Algoritmo di tabella a scala]])
		- [[Analisi lessicale]], [[Lex]], [[Pumping lemma]]
		- [[Analisi sintattica]], [[Grammatiche libere]], [[Automa a pila]] ([[NPDA]], [[DPDA]]), [[Linguaggio libero]], [[Pumping theorem]]
		- [[Classificazione di Chomsky]]
		- [[DPDA]], [[Linguaggio libero deterministico]], [[Semplificazione delle grammatiche]]
		- [[Parser]], [[Parser top-down]] ([[Look-ahead]], [[First e follow]], [[Tabella di parsing LL(1)]], [[Grammatiche LL(1)]], [[Tabella di parsing LL(k)]], [[Grammatiche LL(k)]]), [[Parser bottom-up]]
		- parser: costruzione di analizzatori sintattici
		- fondamenti: esistono vincoli che un compilatore non può verificare; proprietà indecidibili; Macchine di Turing
	- mod. 2
		- [[Nome]], [[Oggetto denotabile]], [[Binding]], [[Blocco]], [[Ambiente]], [[Aliasing]], [[Scope]], [[Regole di visibilita' dei nomi]]
			- [[Scope statico]], [[Scope dinamico]]
		- [[Allocazione della memoria dei programmi]]
			- [[Allocazione statica della memoria dei programmi]]
			- [[Allocazione dinamica della memoria dei programmi]]
				- [[Stack]], [[Record di attivazione]]
				- [[Heap]], [[Lista libera]], [[Liste libere multiple]]
					- [[Frammentazione]], [[Frammentazione interna]], [[Frammentazione esterna]]
					- [[Best fit]], [[First fit]]
					- [[Buddy system]], [[Fibonacci system]]
			- [[Catena statica]], [[Display]]
			- [[A-list]], [[CRT]]
		- strutturare il controllo
			- [[Espressione]], [[Comando]], [[Variabile]], [[Assegnamento]]
		- astrarre sul controllo
			- [[Passaggio dei parametri]]
			- [[Chiusura]]
			- [[Funzione di ordine superiore]]
		- [[Eccezione]]
	- mod. 3
		- [[Sistema di tipi]], [[Tipi di dato]]
		- strutturare i dati
		- astrarre i dati
		- paradigma orientato agli oggetti
		- cenni al paradigma funzionale
		- cenni al paradigma logico
		- cenni alla programmazione concorrente e service-oriented

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/linguaggi-di-programmazione SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/linguaggi-di-programmazione SORT file.ctime DESC -->

| Note                                                                                                               | Status                             |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [[2. notes/Linguaggio LL(k).md\|Linguaggio LL(k)]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tabella di parsing LL(k).md\|Tabella di parsing LL(k)]]                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche LL(k).md\|Grammatiche LL(k)]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche LL(1).md\|Grammatiche LL(1)]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tabella di parsing LL(1).md\|Tabella di parsing LL(1)]]                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/First e follow.md\|First e follow]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Fattorizzazione a sinistra.md\|Fattorizzazione a sinistra]]                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Ricorsione sinistra.md\|Ricorsione sinistra]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Simboli inutili.md\|Simboli inutili]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Produzioni unitarie.md\|Produzioni unitarie]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Produzioni epsilon.md\|Produzioni epsilon]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Forma normale di Greibach.md\|Forma normale di Greibach]]                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Forma normale di Chomsky.md\|Forma normale di Chomsky]]                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Semplificazione delle grammatiche.md\|Semplificazione delle grammatiche]]                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Parser bottom-up.md\|Parser bottom-up]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Parser.md\|Parser]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/DPDA.md\|DPDA]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Look-ahead.md\|Look-ahead]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Parser top-down.md\|Parser top-down]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio libero deterministico.md\|Linguaggio libero deterministico]]                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Analisi sintattica.md\|Analisi sintattica]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio regolare.md\|Linguaggio regolare]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Classificazione di Chomsky.md\|Classificazione di Chomsky]]                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Pumping theorem.md\|Pumping theorem]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio libero.md\|Linguaggio libero]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/NPDA.md\|NPDA]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Equivalenza tra NFA ed espressioni regolari.md\|Equivalenza tra NFA ed espressioni regolari]]           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Semantica statica.md\|Semantica statica]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Analisi lessicale.md\|Analisi lessicale]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Diagramma di transizione.md\|Diagramma di transizione]]                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Costruzione per sottoinsiemi.md\|Costruzione per sottoinsiemi]]                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Algoritmo di tabella a scala.md\|Algoritmo di tabella a scala]]                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Lex.md\|Lex]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Pumping lemma.md\|Pumping lemma]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Semantica operazionale strutturata.md\|Semantica operazionale strutturata]]                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Struttura di un compilatore.md\|Struttura di un compilatore]]                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/NFA.md\|NFA]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/DFA.md\|DFA]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Equivalenza tra NFA e grammatiche regolari.md\|Equivalenza tra NFA e grammatiche regolari]]             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche.md\|Grammatiche]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Minimizzazione di DFA.md\|Minimizzazione di DFA]]                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipi composti.md\|Tipi composti]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipo estensionale.md\|Tipo estensionale]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipo intensionale.md\|Tipo intensionale]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipi di base.md\|Tipi di base]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Sistema di tipi.md\|Sistema di tipi]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipaggio inferred.md\|Tipaggio inferred]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipaggio manifest.md\|Tipaggio manifest]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipaggio dinamico.md\|Tipaggio dinamico]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipaggio statico.md\|Tipaggio statico]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Eccezione.md\|Eccezione]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Shallow binding.md\|Shallow binding]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Deep binding.md\|Deep binding]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Funzione di ordine superiore.md\|Funzione di ordine superiore]]                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Chiusura.md\|Chiusura]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per nome.md\|Passaggio per nome]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per valore-risultato.md\|Passaggio per valore-risultato]]                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per risultato.md\|Passaggio per risultato]]                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio dei parametri.md\|Passaggio dei parametri]]                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Iterazione.md\|Iterazione]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Ricorsione in coda.md\|Ricorsione in coda]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Comando.md\|Comando]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio di programmazione funzionale.md\|Linguaggio di programmazione funzionale]]                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Variabile.md\|Variabile]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Ricorsione.md\|Ricorsione]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Assegnamento.md\|Assegnamento]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Notazione postfissa.md\|Notazione postfissa]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Notazione infissa.md\|Notazione infissa]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Notazione prefissa.md\|Notazione prefissa]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/CRT.md\|CRT]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/A-list.md\|A-list]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Display.md\|Display]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Catena statica.md\|Catena statica]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Fibonacci system.md\|Fibonacci system]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Buddy system.md\|Buddy system]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Liste libere multiple.md\|Liste libere multiple]]                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Lista libera.md\|Lista libera]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Record di attivazione.md\|Record di attivazione]]                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Allocazione dinamica della memoria dei programmi.md\|Allocazione dinamica della memoria dei programmi]] | <ul><li>#status/finished</li></ul> |
| [[2. notes/Allocazione statica della memoria dei programmi.md\|Allocazione statica della memoria dei programmi]]   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Stack.md\|Stack]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Allocazione della memoria dei programmi.md\|Allocazione della memoria dei programmi]]                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Regole di visibilita' dei nomi.md\|Regole di visibilita' dei nomi]]                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Scope dinamico.md\|Scope dinamico]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Scope statico.md\|Scope statico]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Aliasing.md\|Aliasing]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Blocco.md\|Blocco]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Ambiente.md\|Ambiente]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Binding.md\|Binding]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Oggetto denotabile.md\|Oggetto denotabile]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Nome.md\|Nome]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Derivazione canonica destra.md\|Derivazione canonica destra]]                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Derivazione canonica sinistra.md\|Derivazione canonica sinistra]]                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Automa a pila.md\|Automa a pila]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Equivalenze regolari.md\|Equivalenze regolari]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Equivalenza tra DFA e grammatiche regolari.md\|Equivalenza tra DFA e grammatiche regolari]]             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche regolari.md\|Grammatiche regolari]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Macchina astratta.md\|Macchina astratta]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio accettato.md\|Linguaggio accettato]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Automa a stati finiti.md\|Automa a stati finiti]]                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio denotato da un'espressione regolare.md\|Linguaggio denotato da un'espressione regolare]]     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Espressione regolare.md\|Espressione regolare]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Discipline di valutazione.md\|Discipline di valutazione]]                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Computazione.md\|Computazione]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Sistema di transizione.md\|Sistema di transizione]]                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Analisi semantica.md\|Analisi semantica]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Semantica dinamica.md\|Semantica dinamica]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Albero concreto.md\|Albero concreto]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Sintassi concreta.md\|Sintassi concreta]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Sintassi astratta.md\|Sintassi astratta]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio ambiguo.md\|Linguaggio ambiguo]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatica ambigua.md\|Grammatica ambigua]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Albero sintattico.md\|Albero sintattico]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Albero di derivazione.md\|Albero di derivazione]]                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche equivalenti.md\|Grammatiche equivalenti]]                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio generato.md\|Linguaggio generato]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Derivazione.md\|Derivazione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Grammatiche libere.md\|Grammatiche libere]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Rappresentazione finita di un linguaggio.md\|Rappresentazione finita di un linguaggio]]                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Descrivere un linguaggio di programmazione.md\|Descrivere un linguaggio di programmazione]]             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Implementazione.md\|Implementazione]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio formale.md\|Linguaggio formale]]                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Realizzazione di una macchina astratta.md\|Realizzazione di una macchina astratta]]                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio di programmazione.md\|Linguaggio di programmazione]]                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Pragmatica.md\|Pragmatica]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Semantica.md\|Semantica]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Sintassi.md\|Sintassi]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Funzione parziale.md\|Funzione parziale]]                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Macchina fisica.md\|Macchina fisica]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Interprete.md\|Interprete]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio macchina.md\|Linguaggio macchina]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio di programmazione logico.md\|Linguaggio di programmazione logico]]                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio di programmazione dichiarativo.md\|Linguaggio di programmazione dichiarativo]]               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Linguaggio di programmazione imperativo.md\|Linguaggio di programmazione imperativo]]                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Categorie di linguaggi di programmazione.md\|Categorie di linguaggi di programmazione]]                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Evoluzione dei linguaggi di programmazione.md\|Evoluzione dei linguaggi di programmazione]]             | <ul><li>#status/finished</li></ul> |
| [[2. notes/First fit.md\|First fit]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Best fit.md\|Best fit]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[2. notes/Frammentazione esterna.md\|Frammentazione esterna]]                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per costante.md\|Passaggio per costante]]                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per riferimento.md\|Passaggio per riferimento]]                                               | <ul><li>#status/finished</li></ul> |
| [[2. notes/Passaggio per valore.md\|Passaggio per valore]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Scope.md\|Scope]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Frammentazione interna.md\|Frammentazione interna]]                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Dichiarazione.md\|Dichiarazione]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Frammentazione.md\|Frammentazione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Espressione.md\|Espressione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Type safety.md\|Type safety]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Tipi di dato.md\|Tipi di dato]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Compilatore.md\|Compilatore]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Heap.md\|Heap]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Array.md\|Array]]                                                                                       | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale]()
- [dynamik]()
- eserciziari