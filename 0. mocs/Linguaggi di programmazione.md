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

| Lezione                    | Note                                              |
| -------------------------- | ------------------------------------------------- |
| [[Lecture 10042025131105]] | <ul><li>[[Linguaggi di programmazione]]</li></ul> |
<!-- SerializedQuery END -->


### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/linguaggi-di-programmazione SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/linguaggi-di-programmazione SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 10042025131105]] | 10-04-2025 13:11:05 |
| [[Lecture 09042025110710]] | 09-04-2025 11:07:10 |
| [[Lecture 03042025131202]] | 03-04-2025 13:12:02 |
| [[Lecture 19032025113725]] | 19-03-2025 11:37:25 |
| [[Lecture 02042025112213]] | 02-04-2025 11:22:13 |
| [[Lecture 12032025111631]] | 12-03-2025 11:16:31 |
| [[Lecture 17092024110611]] | 17-09-2024 11:06:11 |
| [[Lecture 27022025131944]] | 27-02-2025 13:19:44 |
| [[Lecture 26022025111603]] | 26-02-2025 11:16:03 |
| [[Lecture 05032025111458]] | 05-03-2025 11:14:58 |
| [[Lecture 20022025131602]] | 20-02-2025 13:16:02 |
| [[Lecture 19022025111150]] | 19-02-2025 11:11:50 |
| [[Lecture 21112024121059]] | 21-11-2024 12:10:59 |
| [[Lecture 12112024110924]] | 12-11-2024 11:09:24 |
| [[Lecture 07112024120244]] | 07-11-2024 12:02:44 |
| [[Lecture 05112024110833]] | 05-11-2024 11:08:33 |
| [[Lecture 17102024120438]] | 17-10-2024 12:04:38 |
| [[Lecture 15102024110302]] | 15-10-2024 11:03:02 |
| [[Lecture 24102024120228]] | 24-10-2024 12:02:28 |
| [[Lecture 22102024110521]] | 22-10-2024 11:05:21 |
| [[Lecture 10102024120505]] | 10-10-2024 12:05:05 |
| [[Lecture 08102024111650]] | 08-10-2024 11:16:50 |
| [[Lecture 18102024090854]] | 18-10-2024 09:08:54 |
| [[Lecture 03102024120247]] | 03-10-2024 12:02:47 |
| [[Lecture 01102024110253]] | 01-10-2024 11:02:53 |
| [[Lecture 26092024120454]] | 26-09-2024 12:04:54 |
| [[Lecture 24092024110820]] | 24-09-2024 11:08:20 |
| [[Lecture 19092024125624]] | 19-09-2024 12:56:24 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/linguaggi-di-programmazione AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/linguaggi-di-programmazione AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[Lecture 24102024120228]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 22102024110521]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21112024121059]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 18102024090854]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 12112024110924]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 10042025131105]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 09042025110710]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 07112024120244]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 05112024110833]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->


## Note
- Argomenti
	- mod. 1
		- [[Linguaggio di programmazione]] (evoluzione, categorie, confronti)
		- [[Macchina astratta|Macchine astratte]], [[Linguaggio macchina]], [[Interprete]], [[Compilatore]]
		- [[Descrivere un linguaggio di programmazione]], [[Sintassi]], [[Semantica]], [[Pragmatica]], [[Implementazione]], [[Linguaggio formale]]
		- [[Rappresentazione finita di un linguaggio]], [[Grammatiche]], [[Derivazione]], [[Linguaggio generato]], [[Albero di derivazione]], [[Grammatica ambigua]]
		- [[Semantica statica]], [[Semantica dinamica]]
		- [[Struttura di un compilatore]]
		- [[Semantica operazionale strutturata]]
		- [[Espressione regolare]], [[Automa a stati finiti]] ([[NFA]], [[DFA]]), [[Grammatiche regolari]], [[Linguaggio regolare]], [[Equivalenze regolari]]
		- [[Analisi lessicale]], [[Lex]], [[Pumping lemma]]
		- grammatiche libere da contesto, automi a pila: equivalenze e risultati principali
		- grammatiche libere deterministiche: algoritmi di riconoscimento e costruzione dell'albero di derivazione
		- parser: costruzione di analizzatori sintattici
		- fondamenti: esistono vincoli che un compilatore non può verificare; proprietà indecidibili; Macchine di Turing
	- mod. 2
		- [[Nome]], [[Oggetto denotabile]], [[Binding]], [[Blocco]], [[Ambiente]], [[Aliasing]], [[Scope]], [[Regole di visibilita' dei nomi]]
			- [[Scope statico]], [[Scope dinamico]]
		- [[Allocazione della memoria]]
			- [[Allocazione statica della memoria]]
			- [[Allocazione dinamica della memoria]]
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

| Note                                                                                                           | Status                             |
| -------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[Tipi composti]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Array]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Eccezione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Shallow binding]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Sistema di tipi]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Tipaggio dinamico]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Tipaggio inferred]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Tipi di base]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Tipo estensionale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Deep binding]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Funzione di ordine superiore]]                                     | <ul><li>#status/finished</li></ul> |
| [[Tipaggio manifest]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Tipaggio statico]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Tipo intensionale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Type safety]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Ricorsione]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Tipi di dato]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Chiusura]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Passaggio dei parametri]]                                               | <ul><li>#status/finished</li></ul> |
| [[Passaggio per nome]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Passaggio per risultato]]                                               | <ul><li>#status/finished</li></ul> |
| [[Passaggio per valore-risultato]]                                 | <ul><li>#status/finished</li></ul> |
| [[Passaggio per costante]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Passaggio per riferimento]]                                           | <ul><li>#status/finished</li></ul> |
| [[Passaggio per valore]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Ricorsione in coda]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Binding]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Comando]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Notazione postfissa]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Variabile]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Notazione prefissa]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Notazione infissa]]                                                           | <ul><li>#status/finished</li></ul> |
| [[CRT]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Espressione]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[A-list]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Scope dinamico]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Display]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Catena statica]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Scope statico]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Fibonacci system]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Buddy system]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Liste libere multiple]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Lista libera]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Best fit]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[First fit]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Frammentazione esterna]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Frammentazione interna]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Frammentazione]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Heap]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Record di attivazione]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Allocazione statica della memoria]]                           | <ul><li>#status/finished</li></ul> |
| [[Allocazione della memoria]]                                           | <ul><li>#status/finished</li></ul> |
| [[Aliasing]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Regole di visibilita' dei nomi]]                                 | <ul><li>#status/finished</li></ul> |
| [[Nome]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Oggetto denotabile]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Scope]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Blocco]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Ambiente]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Dichiarazione]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Struttura di un compilatore]]                                       | <ul><li>#status/finished</li></ul> |
| [[NPDA]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Automa a pila]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Derivazione canonica destra]]                                       | <ul><li>#status/finished</li></ul> |
| [[Derivazione canonica sinistra]]                                   | <ul><li>#status/finished</li></ul> |
| [[Albero di derivazione]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Derivazione]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Analisi sintattica]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Linguaggio regolare]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Pumping lemma]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Lex]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Minimizzazione di DFA]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di tabella a scala]]                                     | <ul><li>#status/finished</li></ul> |
| [[Analisi lessicale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Equivalenze regolari]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Equivalenza tra DFA e grammatiche regolari]]         | <ul><li>#status/finished</li></ul> |
| [[Grammatiche regolari]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Equivalenza tra NFA e grammatiche regolari]]         | <ul><li>#status/finished</li></ul> |
| [[Equivalenza tra NFA ed espressioni regolari]]       | <ul><li>#status/finished</li></ul> |
| [[Costruzione per sottoinsiemi]]                                     | <ul><li>#status/finished</li></ul> |
| [[NFA]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[DFA]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Automa a stati finiti]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Espressione regolare]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Linguaggio accettato]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Diagramma di transizione]]                                             | <ul><li>#status/finished</li></ul> |
| [[Linguaggio denotato da un'espressione regolare]] | <ul><li>#status/finished</li></ul> |
| [[Semantica operazionale strutturata]]                         | <ul><li>#status/finished</li></ul> |
| [[Discipline di valutazione]]                                           | <ul><li>#status/finished</li></ul> |
| [[Computazione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Sistema di transizione]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Analisi semantica]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Semantica dinamica]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Semantica statica]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Compilatore]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Interprete]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Realizzazione di una macchina astratta]]                 | <ul><li>#status/finished</li></ul> |
| [[Albero concreto]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Grammatica ambigua]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Linguaggio ambiguo]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Sintassi astratta]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Sintassi concreta]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Albero sintattico]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Grammatiche libere]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Linguaggio generato]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Grammatiche equivalenti]]                                               | <ul><li>#status/finished</li></ul> |
| [[Grammatiche]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Rappresentazione finita di un linguaggio]]             | <ul><li>#status/finished</li></ul> |
| [[Linguaggio di programmazione]]                                     | <ul><li>#status/finished</li></ul> |
| [[Descrivere un linguaggio di programmazione]]         | <ul><li>#status/finished</li></ul> |
| [[Linguaggio formale]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Implementazione]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Pragmatica]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Sintassi]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Funzione parziale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Macchina astratta]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Macchina fisica]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Linguaggio macchina]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Evoluzione dei linguaggi di programmazione]]         | <ul><li>#status/finished</li></ul> |
| [[Categorie di linguaggi di programmazione]]             | <ul><li>#status/finished</li></ul> |
| [[Linguaggio di programmazione dichiarativo]]           | <ul><li>#status/finished</li></ul> |
| [[Linguaggio di programmazione logico]]                       | <ul><li>#status/finished</li></ul> |
| [[Linguaggio di programmazione funzionale]]               | <ul><li>#status/finished</li></ul> |
| [[Linguaggio di programmazione imperativo]]               | <ul><li>#status/finished</li></ul> |
| [[Semantica]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Iterazione]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Stack]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Assegnamento]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Allocazione dinamica della memoria]]                         | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->


## Referenze
- [virtuale]()
- [dynamik]()
- eserciziari