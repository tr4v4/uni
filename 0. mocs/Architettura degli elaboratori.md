---
tags:
  - category/moc
  - status/finished
  - topic/architettura-degli-elaboratori
date: 18-09-2023 12:56:24
---
# Architettura degli elaboratori
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/architettura-degli-elaboratori
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/architettura-degli-elaboratori
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/architettura-degli-elaboratori AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
Argomenti:
- [[Storia degli elaboratori]]
- [[Architettura di von Neumann]]
- [[Parallelismo]]
- [[Macchina multilivello]]
- Livello logico digitale
	- [[Porte logiche]] e [[Circuiti combinatori]]
	- [[Rappresentazione dell'informazione]]
		- [[Codici correttori]]
	- [[ALU HACK]]
	- [[Circuiti sequenziali]]
	- [[Memorie]]
- [[Microarchitettura]]
	- [[Microarchitettura HACK]]
	- [[Cache]]
	- [[Pipelining]]
- [[ISA]]
	- [[Istruzioni ISA]]
		- [[ISA HACK]]
		- [[Computer HACK]]
	- [[Invocazione di procedura]]
		- [[Record di attivazione]]
		- [[Trap]]
		- [[Interrupt]]
- [[SO]]
	- Compiti
		- [[Paginazione]]
		- [[Segmentazione]]
		- [[Frammentazione]]
		- [[Combinazione segmentazione-paginazione]]
	- [[Workflow di compilazione]]
		- [[Linker]]
			- [[Linking statico]]
			- [[Linking dinamico]]
		- [[Compilazione diretta]]
		- [[Compilazione a 2 livelli]]
	- [[Virtual machine]]
		- [[Virtual machine HACK]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/architettura-degli-elaboratori
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=53548)
- [dynamik](https://dynamik.vercel.app/architettura-degli-elaboratori)