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
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                                                                                                                                                                                                                                                                                       |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Lecture 05112024094126]] | <ul><li>[[Calcolo numerico]]</li><li>[[Algoritmi per la risoluzione di sistemi lineari]]</li><li>[[CGLS]]</li><li>[[Metodo dei gradienti coniugati]]</li></ul> |
<!-- SerializedQuery END -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 05112024094126]] | 05-11-2024 09:41:26 |
| [[Lecture 11112024131700]] | 11-11-2024 13:17:00 |
| [[Lecture 12112024091405]] | 12-11-2024 09:14:05 |
| [[Lecture 04112024131513]] | 04-11-2024 13:15:13 |
| [[Lecture 22102024092339]] | 22-10-2024 09:23:39 |
| [[Lecture 21102024132104]] | 21-10-2024 13:21:04 |
| [[Lecture 15102024091721]] | 15-10-2024 09:17:21 |
| [[Lecture 14102024131954]] | 14-10-2024 13:19:54 |
| [[Lecture 08102024093421]] | 08-10-2024 09:34:21 |
| [[Lecture 07102024132143]] | 07-10-2024 13:21:43 |
| [[Lecture 30092024131914]] | 30-09-2024 13:19:14 |
| [[Lecture 26092024092021]] | 26-09-2024 09:20:21 |
| [[Lecture 24092024092227]] | 24-09-2024 09:22:27 |
| [[Lecture 23092024132935]] | 23-09-2024 13:29:35 |
| [[Lecture 16092024131302]] | 16-09-2024 13:13:02 |
| [[Lecture 16092024152034]] | 16-09-2024 15:20:34 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/calcolo-numerico AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/calcolo-numerico AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[Lecture 12112024091405]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 11112024131700]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->

## Note
- Argomenti
	- Numeri finiti ed errori
		- [[Codifica floating-point]]
		- [[Errore nel calcolo numerico]]
		- [[Aritmetica floating-point]]
	- Algebra lineare numerica
		- [[Algoritmi per il calcolo delle radici di una funzione]]
		- [[Algoritmi per la risoluzione di sistemi lineari]]
		- [[Problema dei minimi quadrati]]
	- [[Approssimazione di dati]]
		- [[Approssimazione ai minimi quadrati]]
		- [[Regolarizzazione]]
		- [[Interpolazione]]
	- [[Ottimizzazione di dati]]
		- [[Metodo di discesa del gradiente]]
		- [[Metodo dei gradienti coniugati]]
	- [[Problemi inversi]]
		- [[Imaging]]
	- Introduzione, esercitazioni e applicazioni a Python

- Homeworks
	- [[Calcolo numerico - HW. 1]]
	- [[Calcolo numerico - HW. 2]]
	- [[Calcolo numerico - HW. 3]]

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/calcolo-numerico SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/calcolo-numerico SORT file.ctime DESC -->

| Note                                                                                                                         | Status                             |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[CGLS]]                                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Metodo dei gradienti coniugati]]                                               | <ul><li>#status/finished</li></ul> |
| [[Problemi inversi]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Principio di massima discrepanza]]                                           | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione ai valori singolari troncata]]                   | <ul><li>#status/finished</li></ul> |
| [[Condizioni discrete di Picard]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Condizione di Wolfe]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Metodo di discesa del gradiente]]                                             | <ul><li>#status/finished</li></ul> |
| [[Funzione coerciva]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Funzione convessa]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Nodi di Chebyshev-Gauss-Lobatto]]                                             | <ul><li>#status/finished</li></ul> |
| [[Interpolazione]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Ottimizzazione di dati]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Metodo LASSO]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Regolarizzazione alla Tikhonov]]                                               | <ul><li>#status/finished</li></ul> |
| [[Regolarizzazione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Approssimazione ai minimi quadrati]]                                       | <ul><li>#status/finished</li></ul> |
| [[Problema test]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Approssimazione di dati]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione ai valori singolari]]                                     | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione agli autovalori]]                                             | <ul><li>#status/finished</li></ul> |
| [[Problema dei minimi quadrati]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Norma matriciale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Norma vettoriale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Numero di condizione]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Errore inerente]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Errore algoritmico]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione di Cholesky]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione LU]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmi per la risoluzione di sistemi lineari]]             | <ul><li>#status/finished</li></ul> |
| [[Velocità di convergenza]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di bisezione]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Newton]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Contrazione]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Mappa]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo dell'iterazione di punto fisso]]                           | <ul><li>#status/finished</li></ul> |
| [[Punto fisso]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Errore di troncamento]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo iterativo]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Algoritmi per il calcolo delle radici di una funzione]] | <ul><li>#status/finished</li></ul> |
| [[Aritmetica floating-point]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Errore di arrotondamento]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Errore nel calcolo numerico]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Codifica floating-point]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Conversione binario-decimale]]                                                   | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=65887)
- [dynamik]()
- [github](https://devangelista2.github.io/calcolo-numerico/intro.html)