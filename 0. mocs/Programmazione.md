---
tags:
  - category/moc
  - status/finished
  - topic/programmazione
date: 18-09-2023 15:00:31
---
# Programmazione
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/programmazione
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/programmazione
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/programmazione AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti
	- [[Array]]
		- [[Algoritmo di ordinamento]]
		- [[Ricerca dicotomica]]
	- [[Stringhe]]
	- [[Strutture dati]]
	- [[Puntatori]]
	- [[Strutture dati dinamiche]]
		- [[Liste]]
	- [[Ricorsione]]
	- [[Albero informatico]]
	- [[Classe informatica]] e [[Oggetto informatico]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/programmazione
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=46404)
- [dynamik](https://dynamik.vercel.app/programmazione)