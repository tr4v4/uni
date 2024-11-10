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
| [[Lecture 08112024093603]] | 08-11-2024 09:36:03 |
| [[Lecture 25102024091600]] | 25-10-2024 09:16:00 |
| [[Lecture 07112024092537]] | 07-11-2024 09:25:37 |
| [[Lecture 24102024091305]] | 24-10-2024 09:13:05 |
| [[Lecture 17102024091631]] | 17-10-2024 09:16:31 |
| [[Lecture 16102024132343]] | 16-10-2024 13:23:43 |
| [[Lecture 10102024092110]] | 10-10-2024 09:21:10 |
| [[Lecture 11102024092906]] | 11-10-2024 09:29:06 |
| [[Lecture 03102024092157]] | 03-10-2024 09:21:57 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/sistemi-operativi AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/sistemi-operativi AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione                                                           | Status                            |
| ----------------------------------------------------------------- | --------------------------------- |
| [[Lecture 08112024093603]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 07112024092537]] | <ul><li>#status/pending</li></ul> |
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

| Note                                                                             | Status                             |
| -------------------------------------------------------------------------------- | ---------------------------------- |
| [[C]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Semafori binari]]                                 | <ul><li>#status/finished</li></ul> |
| [[Semafori]]                                               | <ul><li>#status/finished</li></ul> |
| [[Test&Set]]                                               | <ul><li>#status/finished</li></ul> |
| [[Spinlock]]                                               | <ul><li>#status/finished</li></ul> |
| [[Disabilitazione degli interrupt]] | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Peterson]]                     | <ul><li>#status/ongoing</li></ul>  |
| [[Unix]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Azione atomica]]                                   | <ul><li>#status/finished</li></ul> |
| [[Sezione critica]]                                 | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Dekker]]                         | <ul><li>#status/finished</li></ul> |
| [[Deadlock]]                                               | <ul><li>#status/finished</li></ul> |
| [[Mutua esclusione]]                               | <ul><li>#status/finished</li></ul> |
| [[Proprietà liveness]]                           | <ul><li>#status/finished</li></ul> |
| [[Proprietà safety]]                               | <ul><li>#status/finished</li></ul> |
| [[Starvation]]                                           | <ul><li>#status/finished</li></ul> |
| [[Problema della sezione critica]]   | <ul><li>#status/finished</li></ul> |
| [[Proprietà di un programma]]             | <ul><li>#status/finished</li></ul> |
| [[Cross compiler]]                                   | <ul><li>#status/finished</li></ul> |
| [[GCC]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Multiprogramming]]                               | <ul><li>#status/finished</li></ul> |
| [[Race condition]]                                   | <ul><li>#status/finished</li></ul> |
| [[Distributed processing]]                   | <ul><li>#status/finished</li></ul> |
| [[Esecuzione concorrente]]                   | <ul><li>#status/finished</li></ul> |
| [[Multiprocessing]]                                 | <ul><li>#status/finished</li></ul> |
| [[Concorrenza]]                                         | <ul><li>#status/finished</li></ul> |
| [[Processo]]                                               | <ul><li>#status/finished</li></ul> |
| [[Programma]]                                             | <ul><li>#status/finished</li></ul> |
| [[Assioma di finite progress]]           | <ul><li>#status/finished</li></ul> |
| [[Sistema operativo]]                             | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale]()
- [dynamik]()
- [sito del corso](https://www.cs.unibo.it/~renzo/so/)
- eserciziari