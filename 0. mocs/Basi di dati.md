---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/basi-di-dati
date: 21-09-2025 20:49:55
---
# Basi di dati
---
## Lezioni
### Ultima lezione
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/basi-di-dati SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/basi-di-dati SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                        |
| ----------------------------------------------------------------- | ----------------------------------------------------------- |
| [[1. lectures/Lecture 17102025151336.md\|Lecture 17102025151336]] | <ul><li>[[0. mocs/Basi di dati.md\|Basi di dati]]</li></ul> |
<!-- SerializedQuery END -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/basi-di-dati SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/basi-di-dati SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[1. lectures/Lecture 17102025151336.md\|Lecture 17102025151336]] | 17-10-2025 15:13:36 |
| [[1. lectures/Lecture 16102025151651.md\|Lecture 16102025151651]] | 16-10-2025 15:16:51 |
| [[1. lectures/Lecture 09102025151427.md\|Lecture 09102025151427]] | 09-10-2025 15:14:27 |
| [[1. lectures/Lecture 08102025101345.md\|Lecture 08102025101345]] | 08-10-2025 10:13:45 |
| [[1. lectures/Lecture 02102025151515.md\|Lecture 02102025151515]] | 02-10-2025 15:15:15 |
| [[1. lectures/Lecture 01102025093247.md\|Lecture 01102025093247]] | 01-10-2025 09:32:47 |
| [[1. lectures/Lecture 26092025151541.md\|Lecture 26092025151541]] | 26-09-2025 15:15:41 |
| [[1. lectures/Lecture 25092025151622.md\|Lecture 25092025151622]] | 25-09-2025 15:16:22 |
| [[1. lectures/Lecture 24092025091104.md\|Lecture 24092025091104]] | 24-09-2025 09:11:04 |
<!-- SerializedQuery END -->



### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/basi-di-dati AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/basi-di-dati AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[1. lectures/Lecture 17102025151336.md\|Lecture 17102025151336]] | <ul><li>#status/pending</li></ul> |
| [[1. lectures/Lecture 16102025151651.md\|Lecture 16102025151651]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->


## Note
- Argomenti
	- - [[Dato]], [[Informazione]]
- [[Database]], [[DBMS]]
	- [[Modellizzazione concettuale]]
	- [[Modellizzazione logica]]
		- [[Modello relazionale dei dati]]
			- [[Vincoli di integrita']]
			- [[Superchiave]], [[Chiave]], [[Chiave primaria]]
			- [[Vincoli di integrita' referenziale]]
	- [[DDL]], [[DML]]
- algebra e calcolo
	- [[Algebra relazionale]]
		- [[Equivalenze nell'algebra relazionale]]
		- [[Viste]], [[Viste virtuali]]
	- [[Calcolo relazionale]]
		- [[Calcolo relazionale sui domini]]
		- [[Calcolo relazionale su tuple con dichiarazioni del range]]
	- [[Limiti del calcolo e dell'algebra relazionale]], [[Chiusura transitiva]], [[Datalog]]
- [[SQL]]
- [[Transazione]]

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/basi-di-dati SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/basi-di-dati SORT file.ctime DESC -->

| Note                                                                                                                               | Status                             |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[2. notes/Modello relazionale dei dati.md\|Modello relazionale dei dati]]                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Datalog.md\|Datalog]]                                                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/SQL.md\|SQL]]                                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Vincoli di integrita' referenziale.md\|Vincoli di integrita' referenziale]]                                             | <ul><li>#status/finished</li></ul> |
| [[2. notes/Chiusura transitiva.md\|Chiusura transitiva]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Limiti del calcolo e dell'algebra relazionale.md\|Limiti del calcolo e dell'algebra relazionale]]                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Calcolo relazionale su tuple con dichiarazioni del range.md\|Calcolo relazionale su tuple con dichiarazioni del range]] | <ul><li>#status/finished</li></ul> |
| [[2. notes/Calcolo relazionale sui domini.md\|Calcolo relazionale sui domini]]                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Calcolo relazionale.md\|Calcolo relazionale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Viste virtuali.md\|Viste virtuali]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Algebra relazionale.md\|Algebra relazionale]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Equivalenze nell'algebra relazionale.md\|Equivalenze nell'algebra relazionale]]                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Viste.md\|Viste]]                                                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/Chiave primaria.md\|Chiave primaria]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[2. notes/Chiave.md\|Chiave]]                                                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Superchiave.md\|Superchiave]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Vincoli di integrita'.md\|Vincoli di integrita']]                                                                       | <ul><li>#status/finished</li></ul> |
| [[2. notes/DBMS.md\|DBMS]]                                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/DML.md\|DML]]                                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/DDL.md\|DDL]]                                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Modellizzazione logica.md\|Modellizzazione logica]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[2. notes/Modellizzazione concettuale.md\|Modellizzazione concettuale]]                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Transazione.md\|Transazione]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[2. notes/Informazione.md\|Informazione]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Dato.md\|Dato]]                                                                                                         | <ul><li>#status/finished</li></ul> |
| [[2. notes/Database.md\|Database]]                                                                                                 | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale]()
- [dynamik]()
- eserciziari