---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/algebra-e-geometria
date: 20-02-2024 08:55:14
---
# Algebra e geometria
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/algebra-e-geometria
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/algebra-e-geometria
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/algebra-e-geometria AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti
	- [[Sistema lineare]]
		- [[Matrice]], [[Algoritmo di Gauss]]
	- [[Spazio vettoriale]], [[Vettore]]
		- [[Sottospazio vettoriale]] ([[Sottospazi vettoriali di R2]], [[Sottospazi vettoriali di R3]], [[Sottospazi vettoriali dei polinomi]])
		- [[Combinazione lineare]], [[Sottospazio generato]]
		- [[Indipendenza lineare]]
		- [[Base]], [[Dimensione]]
		- [[Teorema del completamento]], [[Teorema GEL]]
		- [[Coordinate rispetto a una base]]
	- [[Applicazione lineare]]
		- [[Funzione suriettiva]], [[Funzione iniettiva]]
		- [[Teorema di esistenza e unicità di un'applicazione lineare]]
		- [[Applicazione lineare definita da una matrice]]
		- [[Nucleo]], [[Immagine di funzione]]
		- [[Teorema della dimensione]], [[Isomorfismo]]
		- [[Composizione di applicazioni lineari]]
		- [[Controimmagine]]
		- [[Forme dei sottospazi]]
		- [[Teorema di struttura per sistemi lineari]]
		- [[Teorema di Rouché-Capelli]]
	- [[Determinante]]
		- [[Matrice invertibile]]
		- [[Teorema di Binet]]
		- [[Teorema di Laplace]]
	- [[Cambio di base]]
	- [[Autovalore]] e [[Autovettore]] (e [[Autospazio]])
		- [[Diagonalizzabilità]]
		- [[Polinomio caratteristico]], [[Molteplicità algebrica]], [[Molteplicità geometrica]]
	- [[Ortogonalità]]
		- [[Prodotto scalare]]
		- [[Base ortogonale]], [[Base ortonormale]]
		- [[Sottospazio ortogonale]]
		- [[Proiezione ortogonale]], [[Algoritmo di Gram-Schmidt]]
		- [[Proiezione ortogonale su un sottospazio]]
		- [[Teorema spettrale]]
	- [[Aritmetica modulare]]

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/algebra-e-geometria
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=47400)
- [dynamik](https://dynamik.vercel.app/algebra-e-geometria?from=informatica)
- eserciziari