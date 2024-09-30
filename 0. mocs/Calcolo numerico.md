---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/calcolo-numerico
date: 16-09-2024 10:19:47
---
# Calcolo numerico
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/calcolo-numerico
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/calcolo-numerico
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/calcolo-numerico AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti
	- Numeri finiti ed errori ([[Codifica floating-point]], [[Errore nel calcolo numerico]], [[Aritmetica floating-point]])
	- Algebra lineare numerica
	- Approssimazione di dati
	- Ottimizzazione numerica
	- Risoluzione numerica di problemi inversi mal posti
	- Introduzione, esercitazioni e applicazioni a Python

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/calcolo-numerico
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=65887)
- [dynamik]()
- [github](https://devangelista2.github.io/calcolo-numerico/intro.html)