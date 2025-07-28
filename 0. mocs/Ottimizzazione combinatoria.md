---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/ottimizzazione-combinatoria
date: 18-02-2025 10:28:15
---
# Ottimizzazione combinatoria
---
## Lezioni
### Ultima lezione
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/ottimizzazione-combinatoria SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/ottimizzazione-combinatoria SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                                                       |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| [[Lecture 05052025092115]] | <ul><li>[[Ottimizzazione combinatoria]]</li></ul> |
<!-- SerializedQuery END -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/ottimizzazione-combinatoria  SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/ottimizzazione-combinatoria  SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 05052025092115]] | 05-05-2025 09:21:15 |
| [[Lecture 28042025091551]] | 28-04-2025 09:15:51 |
| [[Lecture 16042025091309]] | 16-04-2025 09:13:09 |
| [[Lecture 14042025091835]] | 14-04-2025 09:18:35 |
| [[Lecture 09042025091244]] | 09-04-2025 09:12:44 |
| [[Lecture 19032025092241]] | 19-03-2025 09:22:41 |
| [[Lecture 12032025091447]] | 12-03-2025 09:14:47 |
| [[Lecture 05032025091441]] | 05-03-2025 09:14:41 |
| [[Lecture 20032025131726]] | 20-03-2025 13:17:26 |
| [[Lecture 03032025091200]] | 03-03-2025 09:12:00 |
| [[Lecture 26022025091753]] | 26-02-2025 09:17:53 |
| [[Lecture 24022025091339]] | 24-02-2025 09:13:39 |
| [[Lecture 19022025091652]] | 19-02-2025 09:16:52 |
| [[Lecture 17022025090125]] | 17-02-2025 09:01:25 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/ottimizzazione-combinatoria  AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/ottimizzazione-combinatoria  AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[Lecture 28042025091551]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 05052025092115]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->


## Note
Argomenti:
- introduzione - [[Problema di ottimizzazione]] e [[Modello|Modelli]]
	- [[Programmazione lineare]], [[Programmazione lineare intera]]
	- [[Vincoli di assegnamento]], [[Vincoli di semi-assegnamento]], [[Insiemi ammissibili]]
	- [[Selezione di sottoinsiemi]], [[Problema di copertura]], [[Problema di partizione]], [[Problema di riempimento]]
	- [[Variabili a valori discreti]]
	- [[Minima quantita' positiva prefissata]], [[Funzione con carico fisso]]
	- [[Valore assoluto in problemi di ottimizzazione]]
	- [[Funzioni lineari a tratti]]
- principali problemi - [[Problema su rete]], [[Problema di flusso]]
	- [[Taglio]], [[Taglio s-t]], [[Grafo residuo]], [[Cammino aumentante]]
	- [[Problema del flusso massimo]]
		- [[Algoritmo di Ford-Fulkerson]]
		- [[Algoritmo di Edmonds-Karp]]
		- [[Algoritmo di Goldberg-Tarjan]]
	- [[Problema del flusso di costo minimo]]
		- [[Algoritmo dei cammini minimi successivi]]
		- [[Algoritmo di cancellazione dei cicli]]
	- [[Problema di accoppiamento]]
- programmazione lineare - algoritmica dei problemi di ottimizzazione di programmazione lineare
	- [[Algoritmi per la programmazione lineare]]
		- [[Teorema di Motzkin]], [[Teorema fondamentale della programmazione lineare]]
		- [[Teoria della dualita']], [[Teorema debole di dualita']]
		- [[Algoritmo del simplesso]]
		- [[Tecnica branch-and-bound]]

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/ottimizzazione-combinatoria SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/ottimizzazione-combinatoria SORT file.ctime DESC -->

| Note                                                                                                                 | Status                             |
| -------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[Algoritmo dei cammini minimi successivi]]                     | <ul><li>#status/finished</li></ul> |
| [[Algoritmo del simplesso]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Direzione di crescita]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Direzione ammissibile]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Teorema debole di dualita']]                                               | <ul><li>#status/finished</li></ul> |
| [[Teoria della dualita']]                                                         | <ul><li>#status/finished</li></ul> |
| [[Teorema fondamentale della programmazione lineare]] | <ul><li>#status/finished</li></ul> |
| [[Teorema di Motzkin]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Algoritmi per la programmazione lineare]]                     | <ul><li>#status/finished</li></ul> |
| [[Problema di accoppiamento di costo minimo]]                 | <ul><li>#status/finished</li></ul> |
| [[Problema di accoppiamento di massima cardinalita']] | <ul><li>#status/finished</li></ul> |
| [[Problema di accoppiamento]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di cancellazione dei cicli]]                           | <ul><li>#status/finished</li></ul> |
| [[Teorema di struttura degli pseudoflussi]]                     | <ul><li>#status/finished</li></ul> |
| [[Problema del flusso di costo minimo]]                             | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Goldberg-Tarjan]]                                           | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Edmonds-Karp]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Ford-Fulkerson]]                                             | <ul><li>#status/finished</li></ul> |
| [[Teorema max-flow min-cut]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Problema del flusso massimo]]                                             | <ul><li>#status/finished</li></ul> |
| [[Cammino aumentante]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Taglio s-t]]                                                                               | <ul><li>#status/ongoing</li></ul>  |
| [[Grafo residuo]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Taglio]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Problema di flusso]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Flusso]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Problema su rete]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Funzioni lineari a tratti]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Valore assoluto in problemi di ottimizzazione]]         | <ul><li>#status/finished</li></ul> |
| [[Funzione con carico fisso]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Minima quantita' positiva prefissata]]                           | <ul><li>#status/finished</li></ul> |
| [[Variabili a valori discreti]]                                             | <ul><li>#status/finished</li></ul> |
| [[Problema di riempimento]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Problema di partizione]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Problema di copertura]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Selezione di sottoinsiemi]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Insiemi ammissibili]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Vincoli di semi-assegnamento]]                                           | <ul><li>#status/finished</li></ul> |
| [[Vincoli di assegnamento]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Programmazione lineare intera]]                                         | <ul><li>#status/finished</li></ul> |
| [[Programmazione lineare]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo euristico]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Algoritmo esatto]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Problema di certificato]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Problema di decisione]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Problema]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Modello di simulazione]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Processo decisionale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Modello basato su gioco]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Problema di ottimizzazione]]                                               | <ul><li>#status/finished</li></ul> |
| [[Modello analitico]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Modello]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Rete]]                                                                                           | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->



## Referenze