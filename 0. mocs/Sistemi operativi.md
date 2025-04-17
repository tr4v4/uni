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
| [[Lecture 10042025153553]] | 10-04-2025 15:35:53 |
| [[Lecture 04042025092728]] | 04-04-2025 09:27:28 |
| [[Lecture 03042025152151]] | 03-04-2025 15:21:51 |
| [[Lecture 19122024091332]] | 19-12-2024 09:13:32 |
| [[Lecture 13032025151745]] | 13-03-2025 15:17:45 |
| [[Lecture 07032025091554]] | 07-03-2025 09:15:54 |
| [[Lecture 21032025091929]] | 21-03-2025 09:19:29 |
| [[Lecture 20032025151643]] | 20-03-2025 15:16:43 |
| [[Lecture 06032025151956]] | 06-03-2025 15:19:56 |
| [[Lecture 21022025091223]] | 21-02-2025 09:12:23 |
| [[Lecture 28022025091715]] | 28-02-2025 09:17:15 |
| [[Lecture 27022025151550]] | 27-02-2025 15:15:50 |
| [[Lecture 20022025151640]] | 20-02-2025 15:16:40 |
| [[Lecture 29112024093415]] | 29-11-2024 09:34:15 |
| [[Lecture 12122024092737]] | 12-12-2024 09:27:37 |
| [[Lecture 22112024091729]] | 22-11-2024 09:17:29 |
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
| [[Lecture 28112024092134]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21112024092345]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21032025091929]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 20032025151643]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 12122024092737]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 10042025153553]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 05122024092457]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 04042025092728]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 03042025152151]] | <ul><li>#status/pending</li></ul> |
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
		- Sistema operativo, [[Sistema parallelo]], [[Sistema distribuito]], [[Sistema real-time]]
		- interfacciamento HW
			- [[Device controller]]
			- [[Interrupt]], [[Gestione degli interrupt]], [[Trap]]
			- [[DMA]]
			- [[RAM]]
			- [[Memory mapped I-O]]
			- [[Memorie]]
				- [[HD]], [[SSD]]
				- [[Cache]]
			- [[Protezione hardware]], [[MMU]], [[Mode switch]]
		- architettura OS
			- [[Kernel]], [[Kernel monolitico]], [[Microkernel]], [[Kernel ibrido]], [[ExoKernel]], [[AnyKernel]]
			- [[Macchina virtuale]]
		- [[Scheduling]], [[Scheduler]]
			- [[PCB]], [[Processo]], [[Thread]]
			- [[Context switch]]
			- [[FCFS]], [[SJF]], [[Round-Robin]]
		- [[Gestione risorse]], [[Deadlock]]
		- gestione memoria
		- gestione memoria secondaria
		- file system
		- sicurezza

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Note                                                                                                                   | Status                             |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[RAM]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Algoritmo del banchiere]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo del banchiere multivaluta]]                               | <ul><li>#status/ongoing</li></ul>  |
| [[Deadlock avoidance]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Binding]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Sistema operativo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Deadlock prevention]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Deadlock recovery]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Insieme di raggiungibilita']]                                               | <ul><li>#status/finished</li></ul> |
| [[Knot]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Deadlock detection]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Grafo di Holt]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Deadlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Risorsa]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Scheduling real-time]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Scheduling]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Scheduling multilivello]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Scheduling a classi di priorita']]                                     | <ul><li>#status/finished</li></ul> |
| [[Scheduling a priorita']]                                                         | <ul><li>#status/finished</li></ul> |
| [[Protezione hardware]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Microkernel]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Macchina virtuale]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[PCB]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[DMA]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Round-Robin]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Scheduler]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Memory mapped I-O]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Kernel]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[File system]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[FCFS]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Kernel monolitico]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Context switch]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Processo]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[SJF]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Gestione degli interrupt]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Unix]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[MMU]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[CD]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[HD]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Cache]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[Memorie]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[SSD]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Kernel ibrido]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Sistema real-time]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Device controller]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Sistema distribuito]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Sistema parallelo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Architettura di von Neumann]]                                               | <ul><li>#status/finished</li></ul> |
| [[Interrupt]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Trap]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Message passing]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Potere espressivo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Filosofi a cena]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Produttore e consumatore]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Monitor]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Lettori e scrittori]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Semafori]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Dekker]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Proprietà di un programma]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Buffer limitato]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Barbiere addormentato]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Problemi classici della programmazione concorrente]] | <ul><li>#status/finished</li></ul> |
| [[Concorrenza]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Semafori binari]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Peterson]]                                                           | <ul><li>#status/ongoing</li></ul>  |
| [[Disabilitazione degli interrupt]]                                       | <ul><li>#status/finished</li></ul> |
| [[Spinlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Test&Set]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Problema della sezione critica]]                                         | <ul><li>#status/finished</li></ul> |
| [[Sezione critica]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Azione atomica]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Starvation]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Mutua esclusione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Proprietà liveness]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Proprietà safety]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[GCC]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Cross compiler]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[C]]                                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Race condition]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Distributed processing]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Multiprocessing]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Multiprogramming]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Esecuzione concorrente]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Assioma di finite progress]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Programma]]                                                                                   | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->


## Referenze
- [virtuale]()
- [dynamik]()
- [sito del corso](https://www.cs.unibo.it/~renzo/so/)
- eserciziari