---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/algoritmi-e-strutture-dati
date: 20-02-2024 00:35:23
---
# Algoritmi e strutture dati
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/algoritmi-e-strutture-dati
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/algoritmi-e-strutture-dati
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/algoritmi-e-strutture-dati AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Introduzione
	- [[Algoritmo]]
- Argomenti
	- [[Notazione asintotica]] e [[Complessità computazionale]]
		- [[Analisi ammortizzata]] ([[Metodo dell'aggregazione]], [[Metodo degli accantonamenti]])
		- [[Equazione di ricorrenza]] ([[Metodo dell'iterazione]], [[Master Theorem]])
	- [[Java]]
	- [[Algoritmo di ordinamento]]
	- [[Strutture dati elementari]]
		- [[Lista]], [[Pila]], [[Coda]]
		- [[Dizionario]] ([[Prototipo vs Implementazione]])
	- [[Albero informatico]]
		- [[Albero binario]]/[[Albero non-binario]] ([[DFS]], [[BFS]])
		- [[Albero binario di ricerca]], [[Albero AVL]]
	- [[Tabella hash]]
		- [[Funzione hash]] ([[Metodo della divisione]], [[Metodo della moltiplicazione]], [[Metodo della codifica algebrica]])
		- [[Collisione hash]] ([[Concatenamento separato]], [[Indirizzamento aperto]])
	- [[Struttura heap]] (+ applicazioni)
		- [[Array heap]]
		- [[Heap sort]]
		- [[Coda con priorità]] ([[D-heap]])
	- [[Struttura union-find]]
		- [[Quick find]]
		- [[Quick union]]
	- [[Tecniche algoritmiche]]
		- [[Divide et impera]]
		- [[Algoritmi greedy]]
		- [[Programmazione dinamica]]
	- [[Grafo]]
		- [[Algoritmi di visita su grafi]]
			- [[BFS su grafi]]
			- [[DFS su grafi]]
				- [[DAG]]
				- [[Ordinamento topologico]]
				- [[Componenti connesse]]
		- [[Minimum spanning tree]]
			- [[Algoritmo di Kruskal]]
			- [[Algoritmo di Prim]]
		- [[Cammino minimo]]
			- [[Algoritmo di Bellman-Ford]]
			- [[Algoritmo di Djikstra]]
			- [[Algoritmo di Floyd-Warshall]]
	- [[Teoria dell'NP-completezza]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/algoritmi-e-strutture-dati
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=47424)
- [dynamik](https://dynamik.vercel.app/algoritmi-e-strutture-di-dati?from=informatica)
- eserciziari