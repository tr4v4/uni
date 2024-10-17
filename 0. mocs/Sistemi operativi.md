---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/sistemi-operativi
date: 16-09-2024 10:45:14
---
# Sistemi operativi
---
## Lezioni
### Ultima lezione
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS NoteFROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC LIMIT 1 -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 17102024091631]] | 17-10-2024 09:16:31 |
| [[Lecture 16102024132343]] | 16-10-2024 13:23:43 |
| [[Lecture 11102024092906]] | 11-10-2024 09:29:06 |
| [[Lecture 10102024092110]] | 10-10-2024 09:21:10 |
| [[Lecture 03102024092157]] | 03-10-2024 09:21:57 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/sistemi-operativi AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/sistemi-operativi AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[Lecture 17102024091631]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 16102024132343]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 11102024092906]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 10102024092110]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->

## Note
- Argomenti
	- 1° parte
		- introduzione ai sistemi operativi
		- programmazione concorrente
	- 2° parte (vero e proprio corso):
		- struttura interna dei sistemi operativi
		- gestione delle risorse - 1
		- gestione delle risorse - 2
		- sicurezza

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Note                                                                   | Status                             |
| ---------------------------------------------------------------------- | ---------------------------------- |
| [[Assioma di finite progress]] | <ul><li>#status/finished</li></ul> |
| [[Processo]]                                     | <ul><li>#status/pending</li></ul>  |
| [[Concorrenza]]                               | <ul><li>#status/pending</li></ul>  |
| [[Sistema operativo]]                   | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale]()
- [dynamik]()
- [sito del corso](https://www.cs.unibo.it/~renzo/so/)
- eserciziari