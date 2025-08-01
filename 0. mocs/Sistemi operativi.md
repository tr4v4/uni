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
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                                   |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [[Lecture 09052025092046]] | <ul><li>[[Sistemi operativi]]</li></ul> |
<!-- SerializedQuery END -->


### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 09052025092046]] | 09-05-2025 09:20:46 |
| [[Lecture 24042025152212]] | 24-04-2025 15:22:12 |
| [[Lecture 23042025152007]] | 23-04-2025 15:20:07 |
| [[Lecture 10042025153553]] | 10-04-2025 15:35:53 |
| [[Lecture 11042025104834]] | 11-04-2025 10:48:34 |
| [[Lecture 03042025152151]] | 03-04-2025 15:21:51 |
| [[Lecture 04042025092728]] | 04-04-2025 09:27:28 |
| [[Lecture 21032025091929]] | 21-03-2025 09:19:29 |
| [[Lecture 20032025151643]] | 20-03-2025 15:16:43 |
| [[Lecture 13032025151745]] | 13-03-2025 15:17:45 |
| [[Lecture 07032025091554]] | 07-03-2025 09:15:54 |
| [[Lecture 06032025151956]] | 06-03-2025 15:19:56 |
| [[Lecture 28022025091715]] | 28-02-2025 09:17:15 |
| [[Lecture 27022025151550]] | 27-02-2025 15:15:50 |
| [[Lecture 21022025091223]] | 21-02-2025 09:12:23 |
| [[Lecture 20022025151640]] | 20-02-2025 15:16:40 |
| [[Lecture 19122024091332]] | 19-12-2024 09:13:32 |
| [[Lecture 12122024092737]] | 12-12-2024 09:27:37 |
| [[Lecture 15112024091205]] | 15-11-2024 09:12:05 |
| [[Lecture 05122024092457]] | 05-12-2024 09:24:57 |
| [[Lecture 29112024093415]] | 29-11-2024 09:34:15 |
| [[Lecture 22112024091729]] | 22-11-2024 09:17:29 |
| [[Lecture 28112024092134]] | 28-11-2024 09:21:34 |
| [[Lecture 21112024092345]] | 21-11-2024 09:23:45 |
| [[Lecture 14112024091601]] | 14-11-2024 09:16:01 |
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
| [[Lecture 28112024092134]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 24042025152212]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 23042025152007]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 21112024092345]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 12122024092737]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 10042025153553]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 09052025092046]] | <ul><li>#status/pending</li></ul> |
| [[Lecture 05122024092457]] | <ul><li>#status/pending</li></ul> |
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
		- [[Risorsa]], [[Deadlock]]
			- [[Deadlock detection]], [[Deadlock recovery]]
			- [[Deadlock prevention]]
			- [[Deadlock avoidance]]
				- [[Algoritmo del banchiere]]
		- [[Gestione della memoria]]
			- [[Binding]], [[Loading dinamico]], [[Linking]]
			- [[MMU]]
			- [[Allocazione]]
				- [[Allocazione dinamica]]
			- [[Paginazione]]
				- [[TLB]]
			- [[Segmentazione]]
			- [[Memoria virtuale]]
				- [[Algoritmi di paginazione]]
				- [[Trashing]]
		- [[I-O|gestione I-O]], gestione memoria secondaria, [[HD]], [[SSD]]
			- [[Disk scheduling]]
			- [[RAID]]
		- [[File system]]
			- [[File]]
			- [[Semantica della coerenza]]
			- [[Partizione di un disco]]
		- sicurezza

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/sistemi-operativi SORT file.ctime DESC -->

| Note                                                                                                                   | Status                             |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| [[Partizione di un disco]]                                                         | <ul><li>#status/finished</li></ul> |
| [[MBR]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Semantica della coerenza]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Estensione]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[File]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[RAID 6]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[RAID 5]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[RAID 4]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[RAID 1]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[RAID 0]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[C-LOOK]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[LOOK]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[SSTF]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Disk scheduling]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Working set]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Trashing]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[LFU]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Algoritmo a stack]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[MIN paginazione]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Anomalia di Belady]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Page fault]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[TLB]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Worst fit]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Next fit]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Allocazione dinamica]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Compattazione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Allocazione]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Linking]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Loading dinamico]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Gestione della memoria]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Indirizzo logico]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Indirizzo fisico]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Cache]]                                                                                           | <ul><li>#status/finished</li></ul> |
| [[Algoritmo del banchiere multivaluta]]                               | <ul><li>#status/ongoing</li></ul>  |
| [[Algoritmo del banchiere]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Deadlock avoidance]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Deadlock prevention]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Deadlock recovery]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Insieme di raggiungibilita']]                                               | <ul><li>#status/finished</li></ul> |
| [[Knot]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Deadlock detection]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Grafo di Holt]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Scheduling real-time]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Scheduling multilivello]]                                                       | <ul><li>#status/finished</li></ul> |
| [[Scheduling a classi di priorita']]                                     | <ul><li>#status/finished</li></ul> |
| [[Scheduling a priorita']]                                                         | <ul><li>#status/finished</li></ul> |
| [[Round-Robin]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[FCFS]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Context switch]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Scheduler]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[PCB]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Scheduling]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Macchina virtuale]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Kernel ibrido]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Microkernel]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Kernel monolitico]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Kernel]]                                                                                         | <ul><li>#status/finished</li></ul> |
| [[File system]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[MMU]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Protezione hardware]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Memory mapped I-O]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[DMA]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Gestione degli interrupt]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Device controller]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Sistema real-time]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Sistema distribuito]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Sistema parallelo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Sistema operativo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Binding]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Potere espressivo]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Message passing]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Monitor]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[Barbiere addormentato]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Lettori e scrittori]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Semafori]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Filosofi a cena]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Produttore e consumatore]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Buffer limitato]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Problemi classici della programmazione concorrente]] | <ul><li>#status/finished</li></ul> |
| [[C]]                                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Semafori binari]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Test&Set]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Spinlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Disabilitazione degli interrupt]]                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Peterson]]                                                           | <ul><li>#status/ongoing</li></ul>  |
| [[Unix]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Azione atomica]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Sezione critica]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Algoritmo di Dekker]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Deadlock]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Mutua esclusione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Proprietà liveness]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Proprietà safety]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Starvation]]                                                                                 | <ul><li>#status/finished</li></ul> |
| [[Problema della sezione critica]]                                         | <ul><li>#status/finished</li></ul> |
| [[Proprietà di un programma]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Cross compiler]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[GCC]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Multiprogramming]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Race condition]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Distributed processing]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Esecuzione concorrente]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Multiprocessing]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Concorrenza]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Processo]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[Programma]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Assioma di finite progress]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Combinazione segmentazione-paginazione]]                         | <ul><li>#status/finished</li></ul> |
| [[Interrupt]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[Linking dinamico]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Paginazione]]                                                                               | <ul><li>#status/finished</li></ul> |
| [[Risorsa]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[SJF]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[I-O]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Best fit]]                                                                                     | <ul><li>#status/finished</li></ul> |
| [[FIFO paginazione]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[First fit]]                                                                                   | <ul><li>#status/finished</li></ul> |
| [[LRU]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Frammentazione esterna]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Segmentazione]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Frammentazione interna]]                                                         | <ul><li>#status/finished</li></ul> |
| [[CD]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[HD]]                                                                                                 | <ul><li>#status/finished</li></ul> |
| [[RAID]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[SSD]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Architettura di von Neumann]]                                               | <ul><li>#status/finished</li></ul> |
| [[Trap]]                                                                                             | <ul><li>#status/finished</li></ul> |
| [[Memoria virtuale]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Memorie]]                                                                                       | <ul><li>#status/finished</li></ul> |
| [[RAM]]                                                                                               | <ul><li>#status/finished</li></ul> |
| [[Linking statico]]                                                                       | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->


## Referenze
- [virtuale]()
- [dynamik]()
- [sito del corso](https://www.cs.unibo.it/~renzo/so/)
- eserciziari