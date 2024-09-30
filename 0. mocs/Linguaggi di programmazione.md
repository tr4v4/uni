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
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/linguaggi-di-programmazione
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/linguaggi-di-programmazione
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/linguaggi-di-programmazione AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti
	- mod. 1
		- [[Linguaggio di programmazione]] (evoluzione, categorie, confronti)
		- [[Macchina astratta|Macchine astratte]], [[Linguaggio macchina]], [[Interprete]], [[Compilatore]]
		- compilatori: struttura generale
		- [[Descrivere un linguaggio di programmazione]] ([[Sintassi]], [[Semantica]], [[Pragmatica]], [[Implementazione]])
		- sintassi (BNF) e semantica (tecnica SOS)
		- grammatiche regolari, automi a stati finiti, espressioni regolari: equivalenze e risultati principali
		- scanner: costruzione di analizzatori lessicali
		- grammatiche libere da contesto, automi a pila: equivalenze e risultati principali
		- grammatiche libere deterministiche: algoritmi di riconoscimento e costruzione dell'albero di derivazione
		- parser: costruzione di analizzatori sintattici
		- fondamenti: esistono vincoli che un compilatore non può verificare; proprietà indecidibili; Macchine di Turing
	- mod. 2
		- nomi
		- gestione della memoria
		- strutturare il controllo
		- astrarre sul controllo
		- parametri e modalità di passaggio
		- strutturare i dati
		- astrarre i dati
		- paradigma orientato agli oggetti
		- cenni al paradigma funzionale
		- cenni al paradigma logico
		- cenni alla programmazione concorrente e service-oriented

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/linguaggi-di-programmazione
SORT file.ctime DESC
```

## Referenze
- [virtuale]()
- [dynamik]()
- eserciziari