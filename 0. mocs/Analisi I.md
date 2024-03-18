---
tags:
  - category/moc
  - status/finished
  - topic/analisi-I
date: 18-09-2023 00:06:24
---
# Analisi I
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/analisi-I
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/analisi-I
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/analisi-I AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Ripasso
	- [[Insiemi numerici]], [[Notazioni]]
	- [[Funzione matematica]]
	- [[Cardinalità]], [[Numerabilità]]
	- [[Calcolo combinatorio]], [[Binomio di Newton]]
	- [[Valore assoluto]]
	- [[Funzione esponenziale]], [[Funzione logaritmica]], [[Trigonometria]]
- Argomenti
	- [[Insiemi numerici]]
		- [[Proprietà di completezza di R]]
		- [[Dimostrazione esistenza e unicità della radice]]
	- Funzioni elementari
		- [[Funzione esponenziale]]
		- [[Funzione logaritmica]]
		- [[Trigonometria]]
	- [[Successione numerica]]
		- [[Limite di successione]]
		- [[Successione monotona]]
		- [[Dimostrazione esistenza numero di Nepero]]
	- [[Funzione matematica]]
		- [[Limite di funzione]]
		- [[Funzioni continue]]
			- [[Teorema degli zeri]]
			- [[Teorema di Weierstrass]], [[Teorema di Weierstrass esteso]]
		- [[Funzioni derivabili]]
		- [[Teorema di Fermat]]
		- 3 teoremi
			- [[Teorema di Rolle]]
			- [[Teorema di Lagrange]]
			- [[Teorema di Cauchy]]
		- [[Grafico di una funzione]], [[Studio di funzione]]
		- [[Teorema di de l'Hopital]]
	- [[Sviluppo in serie di Taylor]]
		- [[O-piccolo]]
		- [[Calcolo dei limiti con Taylor]]
	- [[Integrale]]
		- [[Integrale di Riemann]]
		- [[Teorema della media integrale]]
		- [[Primitiva]]
		- [[Funzione integrale]]
		- [[Teorema fondamentale del calcolo integrale]]
		- [[Teorema di Torricelli-Barrow]]
		- [[Tecniche d'integrazione]]
	- [[Spazio euclideo]] $\mathbb{R}^{n}$
	- [[Funzione a più variabili]]
	- [[Integrale a più variabili]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/analisi-I
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=48318)
- [dynamik](https://dynamik.vercel.app/analisi-matematica/)
- eserciziari