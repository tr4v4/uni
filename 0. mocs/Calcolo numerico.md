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

| Lezione                                                           | Note                                                                 |
| ----------------------------------------------------------------- | -------------------------------------------------------------------- |
| [[Lecture 22102024092339]] | <ul><li>[[Calcolo numerico]]</li></ul> |
<!-- SerializedQuery END -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/calcolo-numerico SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 22102024092339]] | 22-10-2024 09:23:39 |
| [[Lecture 21102024132104]] | 21-10-2024 13:21:04 |
| [[Lecture 14102024131954]] | 14-10-2024 13:19:54 |
| [[Lecture 15102024091721]] | 15-10-2024 09:17:21 |
| [[Lecture 07102024132143]] | 07-10-2024 13:21:43 |
| [[Lecture 08102024093421]] | 08-10-2024 09:34:21 |
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
| [[Lecture 22102024092339]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21102024132104]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 15102024091721]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 14102024131954]] | <ul><li>#status/ongoing</li></ul> |
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
	- Approssimazione di dati
	- Ottimizzazione numerica
	- Risoluzione numerica di problemi inversi mal posti
	- Introduzione, esercitazioni e applicazioni a Python

- Homeworks

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/calcolo-numerico SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/calcolo-numerico SORT file.ctime DESC -->

| Note                                                                                                                         | Status                             |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[Approssimazione ai minimi quadrati]]                                       | <ul><li>#status/ongoing</li></ul>  |
| [[Approssimazione di dati]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Problema test]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Problema dei minimi quadrati]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione agli autovalori]]                                             | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione ai valori singolari]]                                     | <ul><li>#status/finished</li></ul> |
| [[Norma matriciale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Norma vettoriale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Errore inerente]]                                                                             | <ul><li>#status/finished</li></ul> |
| [[Numero di condizione]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Errore algoritmico]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Aritmetica floating-point]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Errore nel calcolo numerico]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Algoritmi per la risoluzione di sistemi lineari]]             | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione di Cholesky]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Fattorizzazione LU]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Velocità di convergenza]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Algoritmi per il calcolo delle radici di una funzione]] | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Newton]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Algoritmo dell'iterazione di punto fisso]]                           | <ul><li>#status/finished</li></ul> |
| [[Contrazione]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Mappa]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Punto fisso]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Errore di troncamento]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di bisezione]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Algoritmo iterativo]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Codifica floating-point]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Errore di arrotondamento]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Conversione binario-decimale]]                                                   | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=65887)
- [dynamik]()
- [github](https://devangelista2.github.io/calcolo-numerico/intro.html)