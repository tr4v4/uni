---
tags:
  - category/moc
  - status/finished
  - topic/logica-per-informatica
date: 19-09-2023 15:46:11
---
# Logica per l'informatica
---
## Lezione
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/logica-per-informatica
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/logica-per-informatica
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/logica-per-informatica AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Logica
	- [[Teoria degli insiemi]]
		- [[Teoria assiomatica degli insiemi]]/[[Teoria naive degli insiemi]]
		- [[ZF]]
		- [[Dimostrazione in teoria assiomatica degli insiemi]]
	- [[Relazione]], [[Funzione matematica]], [[Cardinalità]]
		- [[Relazione di equivalenza]]
		- [[Classe di equivalenza]]
		- [[Insieme quoziente]]
	- [[Deduzione naturale]]
		- [[Regole di inferenza]]
		- [[Conseguenza logica]], [[Teorema di correttezza]], [[Teorema di completezza]]
		- [[Semantica]]
		- [[Logica classica]]
			- [[Logica proposizionale]]
			- [[Logica del primo ordine]]
		- [[Logica intuizionista]]
		- [[Proprietà dei connettivi e quantificatori]]
	- [[Ricorsione strutturale]] e [[Induzione strutturale]]
- Algebra
	- [[Algebra astratta]]
		- [[Astrazione]], [[Generalizzazione]]
		- [[Strutture algebriche]]
		- [[Morfismo]], [[Isomorfismo]]
		- [[Sottostruttura algebrica]], [[Sottoinsieme chiuso]]
		- [[Teorema fondamentale dei morfismi]]
	- Algebra particolare
		- Famiglie di gruppi
			- [[Gruppo modulare]]
			- [[Gruppo diedrale]]
			- [[Gruppo di permutazioni]]
				- [[Teorema di Cayley]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/logica-per-informatica
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=29513)
- [dynamik](https://dynamik.vercel.app/logica-per-informatica)