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

| Lezione                    | Data                |
| -------------------------- | ------------------- |
| [[Lecture 19122024091332]] | 19-12-2024 09:13:32 |
| [[Lecture 12122024092737]] | 12-12-2024 09:27:37 |
| [[Lecture 22112024091729]] | 22-11-2024 09:17:29 |
| [[Lecture 29112024093415]] | 29-11-2024 09:34:15 |
| [[Lecture 05122024092457]] | 05-12-2024 09:24:57 |
| [[Lecture 15112024091205]] | 15-11-2024 09:12:05 |
| [[Lecture 28112024092134]] | 28-11-2024 09:21:34 |
| [[Lecture 14112024091601]] | 14-11-2024 09:16:01 |
| [[Lecture 21112024092345]] | 21-11-2024 09:23:45 |
| [[Lecture 07112024092537]] | 07-11-2024 09:25:37 |
| [[Lecture 08112024093603]] | 08-11-2024 09:36:03 |
| [[Lecture 24102024091305]] | 24-10-2024 09:13:05 |
| [[Lecture 17102024091631]] | 17-10-2024 09:16:31 |
| [[Lecture 25102024091600]] | 25-10-2024 09:16:00 |
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
| [[Lecture 29112024093415]] | <ul><li>#status/ongoing</li></ul> |
| [[Lecture 28112024092134]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21112024092345]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 19122024091332]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 12122024092737]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 05122024092457]] | <ul><li>#status/pending</li></ul> |
<!-- SerializedQuery END -->

## Note
- Argomenti
	- 1° parte
		- [[Sistema operativo]]
		- [[Concorrenza]]
			- [[Processo]], [[Esecuzione concorrente]], [[Race condition]]
			- [[Problema della sezione critica]], [[Proprietà di un programma]]
			- [[Algoritmo di Dekker]], [[Algoritmo di Peterson]]
			- [[Disabilitazione degli interrupt]], [[Spinlock]]
			- [[Semafori]], [[Monitor]], [[Message passing]]
			- [[Problemi classici della programmazione concorrente]]
	- 2° parte (vero e proprio corso):
		- struttura interna dei sistemi operativi
		- gestione delle risorse - 1
		- gestione delle risorse - 2
		- sicurezza

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Note                                                                                                                   | Status                             |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[Monitor]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Filosofi a cena]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Produttore e consumatore]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Buffer limitato]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Lettori e scrittori]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Barbiere addormentato]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Problemi classici della programmazione concorrente]] | <ul><li>#status/finished</li></ul> |
| [[Semafori binari]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Concorrenza]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Semafori]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Test&Set]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Spinlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Disabilitazione degli interrupt]]                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Peterson]]                                                           | <ul><li>#status/ongoing</li></ul>  |
| [[Sezione critica]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Problema della sezione critica]]                                         | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Dekker]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Deadlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Azione atomica]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Starvation]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Mutua esclusione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Proprietà liveness]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Proprietà safety]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Proprietà di un programma]]                                                   | <ul><li>#status/finished</li></ul> |
| [[GCC]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Cross compiler]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[C]]                                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Unix]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Race condition]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Distributed processing]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Multiprocessing]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Multiprogramming]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Esecuzione concorrente]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Assioma di finite progress]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Processo]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Sistema operativo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Programma]]                                                                                   | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale]()
- [dynamik]()
- [sito del corso](https://www.cs.unibo.it/~renzo/so/)
- eserciziari