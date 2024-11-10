---
tags:
  - category/moc
  - status/finished
  - topic/architettura-degli-elaboratori
date: 18-09-2023 12:56:24
---
# Architettura degli elaboratori
---
## Lezioni
### Ultima lezione
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/architettura-degli-elaboratori SORT file.ctime DESC LIMIT 1 -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, file.inlinks AS Note FROM #category/lecture AND #topic/architettura-degli-elaboratori SORT file.ctime DESC LIMIT 1 -->

| Lezione                                                           | Note                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Lecture 02112023130607]] | <ul><li>[[Architettura degli elaboratori]]</li><li>[[ISA]]</li><li>[[Interrupt]]</li><li>[[Invocazione di procedura]]</li><li>[[Istruzioni ISA]]</li><li>[[Modalità di indirizzamento]]</li><li>[[Record di attivazione]]</li><li>[[Trap]]</li></ul> |
<!-- SerializedQuery END -->

### Lista
<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/architettura-degli-elaboratori SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Lezione, date AS Data FROM #category/lecture AND #topic/architettura-degli-elaboratori SORT file.ctime DESC -->

| Lezione                                                           | Data                |
| ----------------------------------------------------------------- | ------------------- |
| [[Lecture 02112023130607]] | 02-11-2023 13:06:07 |
| [[Lecture 16112023133640]] | 16-11-2023 13:36:40 |
| [[Lecture 19102023130600]] | 19-10-2023 13:06:00 |
| [[Lecture 22112023151203]] | 22-11-2023 15:12:03 |
| [[Lecture 09102023132029]] | 09-10-2023 13:20:29 |
| [[Lecture 02102023130256]] | 02-10-2023 13:02:56 |
| [[Lecture 12102023130419]] | 12-10-2023 13:04:19 |
| [[Lecture 11102023151203]] | 11-10-2023 15:12:03 |
| [[Lecture 15112023151146]] | 15-11-2023 15:11:46 |
| [[Lecture 28092023130653]] | 28-09-2023 13:06:53 |
| [[Lecture 27092023150312]] | 27-09-2023 15:03:12 |
| [[Lecture 09112023093612]] | 09-11-2023 09:36:12 |
| [[Lecture 05102023130513]] | 05-10-2023 13:05:13 |
| [[Lecture 25092023130405]] | 25-09-2023 13:04:05 |
| [[Lecture 26102023132035]] | 26-10-2023 13:20:35 |
| [[Lecture 06112023131103]] | 06-11-2023 13:11:03 |
| [[Lecture 20112023130829]] | 20-11-2023 13:08:29 |
| [[Lecture 23112023130836]] | 23-11-2023 13:08:36 |
| [[Lecture 13112023131012]] | 13-11-2023 13:10:12 |
| [[Lecture 16102023125805]] | 16-10-2023 12:58:05 |
| [[Lecture 18092023130242]] | 18-09-2023 13:02:42 |
| [[Lecture 25102023150405]] | 25-10-2023 15:04:05 |
| [[Lecture 21092023130150]] | 21-09-2023 13:01:50 |
| [[Lecture 18102023151217]] | 18-10-2023 15:12:17 |
| [[Lecture 20092023151652]] | 20-09-2023 15:16:52 |
<!-- SerializedQuery END -->

### Da processare
<!-- QueryToSerialize: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/architettura-degli-elaboratori AND (#status/pending OR #status/ongoing) SORT date DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status FROM #category/lecture AND #topic/architettura-degli-elaboratori AND (#status/pending OR #status/ongoing) SORT date DESC -->

| Lezione | Status |
| ------- | ------ |
<!-- SerializedQuery END -->

## Note
Argomenti:
- [[Storia degli elaboratori]]
- [[Architettura di von Neumann]]
- [[Parallelismo]]
- [[Macchina multilivello]]
- Livello logico digitale
	- [[Porte logiche]] e [[Circuiti combinatori]]
	- [[Rappresentazione dell'informazione]]
		- [[Codici correttori]]
	- [[ALU HACK]]
	- [[Circuiti sequenziali]]
	- [[Memorie]]
- [[Microarchitettura]]
	- [[Microarchitettura HACK]]
	- [[Cache]]
	- [[Pipelining]]
- [[ISA]]
	- [[Istruzioni ISA]]
		- [[ISA HACK]]
		- [[Computer HACK]]
	- [[Invocazione di procedura]]
		- [[Record di attivazione]]
		- [[Trap]]
		- [[Interrupt]]
- [[Sistema operativo]]
	- Compiti
		- [[Paginazione]]
		- [[Segmentazione]]
		- [[Frammentazione]]
		- [[Combinazione segmentazione-paginazione]]
	- [[Workflow di compilazione]]
		- [[Linker]]
			- [[Linking statico]]
			- [[Linking dinamico]]
		- [[Compilazione diretta]]
		- [[Compilazione a 2 livelli]]
	- [[Virtual machine]]
		- [[Virtual machine HACK]]

<!-- QueryToSerialize: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/architettura-degli-elaboratori SORT file.ctime DESC -->
<!-- SerializedQuery: TABLE WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status FROM #category/note AND #topic/architettura-degli-elaboratori SORT file.ctime DESC -->

| Note                                                                                             | Status                             |
| ------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [[Linker]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Combinazione segmentazione-paginazione]]   | <ul><li>#status/finished</li></ul> |
| [[Interrupt]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Invocazione di procedura]]                               | <ul><li>#status/finished</li></ul> |
| [[Linking dinamico]]                                               | <ul><li>#status/finished</li></ul> |
| [[Macchina multilivello]]                                     | <ul><li>#status/finished</li></ul> |
| [[Paginazione]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Sistema operativo]]                                             | <ul><li>#status/finished</li></ul> |
| [[Big-endian & Little-endian]]                           | <ul><li>#status/finished</li></ul> |
| [[Codifica floating-point]]                                 | <ul><li>#status/finished</li></ul> |
| [[Conversione binario-decimale]]                       | <ul><li>#status/finished</li></ul> |
| [[Clock]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Dimostrazione R non numerabile]]                   | <ul><li>#status/finished</li></ul> |
| [[Adder]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Half-adder]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Virtual machine HACK]]                                       | <ul><li>#status/finished</li></ul> |
| [[ALU HACK]]                                                               | <ul><li>#status/finished</li></ul> |
| [[CPU]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[CU]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[Ciclo di fetch-decode-execute]]                     | <ul><li>#status/finished</li></ul> |
| [[Mappe di Karnaugh]]                                             | <ul><li>#status/finished</li></ul> |
| [[Parallelismo]]                                                       | <ul><li>#status/finished</li></ul> |
| [[I-O]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[ALU]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Best fit]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Defrag]]                                                                   | <ul><li>#status/finished</li></ul> |
| [[Dirty bit]]                                                             | <ul><li>#status/finished</li></ul> |
| [[FIFO paginazione]]                                               | <ul><li>#status/finished</li></ul> |
| [[First fit]]                                                             | <ul><li>#status/finished</li></ul> |
| [[LRU]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Frammentazione esterna]]                                   | <ul><li>#status/finished</li></ul> |
| [[Algoritmi di paginazione]]                               | <ul><li>#status/finished</li></ul> |
| [[Codifica in eccesso]]                                         | <ul><li>#status/finished</li></ul> |
| [[Complemento a 1]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Complemento a 2]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Conversione binario-ottale-esadecimale]]   | <ul><li>#status/finished</li></ul> |
| [[Modulo e segno]]                                                   | <ul><li>#status/finished</li></ul> |
| [[PLA]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[HDL]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Full-adder]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Multiplexer]]                                                         | <ul><li>#status/finished</li></ul> |
| [[Bit di parità]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Codici correttori]]                                             | <ul><li>#status/finished</li></ul> |
| [[Codifica dei caratteri]]                                   | <ul><li>#status/finished</li></ul> |
| [[Forma canonica booleana]]                                 | <ul><li>#status/finished</li></ul> |
| [[Tabella di verità]]                                             | <ul><li>#status/finished</li></ul> |
| [[Transistor]]                                                           | <ul><li>#status/finished</li></ul> |
| [[Circuiti combinatori]]                                       | <ul><li>#status/finished</li></ul> |
| [[Circuiti digitali]]                                             | <ul><li>#status/finished</li></ul> |
| [[Distanza di Hamming]]                                         | <ul><li>#status/finished</li></ul> |
| [[UNICODE]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[UTF-8]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[ASCII]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Codice di Hamming]]                                             | <ul><li>#status/finished</li></ul> |
| [[Rappresentazione dell'informazione]]           | <ul><li>#status/finished</li></ul> |
| [[Segmentazione]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Frammentazione interna]]                                   | <ul><li>#status/finished</li></ul> |
| [[Frammentazione]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Algebra di Boole]]                                               | <ul><li>#status/finished</li></ul> |
| [[Array computer]]                                                   | <ul><li>#status/finished</li></ul> |
| [[DRAM]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Direct Mapped Cache]]                                         | <ul><li>#status/finished</li></ul> |
| [[Multicomputer]]                                                     | <ul><li>#status/finished</li></ul> |
| [[Multicore]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Multiprocessori]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Pipelining]]                                                           | <ul><li>#status/finished</li></ul> |
| [[SRAM]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Storia degli elaboratori]]                               | <ul><li>#status/finished</li></ul> |
| [[NAND]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Porte logiche]]                                                     | <ul><li>#status/finished</li></ul> |
| [[SR Latch]]                                                               | <ul><li>#status/finished</li></ul> |
| [[CD]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[GPU]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[HD]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[RAID]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[SSD]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[CU HACK]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Computer HACK]]                                                     | <ul><li>#status/finished</li></ul> |
| [[ISA HACK]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Microarchitettura HACK]]                                   | <ul><li>#status/finished</li></ul> |
| [[Architettura HACK]]                                             | <ul><li>#status/finished</li></ul> |
| [[Workflow di compilazione]]                               | <ul><li>#status/finished</li></ul> |
| [[Architettura di von Neumann]]                         | <ul><li>#status/finished</li></ul> |
| [[Principio di astrazione-implementazione]] | <ul><li>#status/finished</li></ul> |
| [[Compilazione a 2 livelli]]                               | <ul><li>#status/finished</li></ul> |
| [[Compilazione diretta]]                                       | <ul><li>#status/finished</li></ul> |
| [[Modalità di indirizzamento]]                           | <ul><li>#status/finished</li></ul> |
| [[Trap]]                                                                       | <ul><li>#status/finished</li></ul> |
| [[Istruzioni ISA]]                                                   | <ul><li>#status/finished</li></ul> |
| [[Memoria virtuale]]                                               | <ul><li>#status/finished</li></ul> |
| [[Pre-fetch]]                                                             | <ul><li>#status/finished</li></ul> |
| [[Registro]]                                                               | <ul><li>#status/finished</li></ul> |
| [[Memorie]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[Stack]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[1-bit register]]                                                   | <ul><li>#status/finished</li></ul> |
| [[ISA]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[Microarchitettura]]                                             | <ul><li>#status/finished</li></ul> |
| [[Circuiti sequenziali]]                                       | <ul><li>#status/finished</li></ul> |
| [[Commutazione a livello]]                                   | <ul><li>#status/finished</li></ul> |
| [[Commutazione al fronte]]                                   | <ul><li>#status/finished</li></ul> |
| [[PC]]                                                                           | <ul><li>#status/finished</li></ul> |
| [[RAM]]                                                                         | <ul><li>#status/finished</li></ul> |
| [[w-bit register]]                                                   | <ul><li>#status/finished</li></ul> |
| [[CISC e RISC]]                                                         | <ul><li>#status/finished</li></ul> |
| [[D Latch]]                                                                 | <ul><li>#status/finished</li></ul> |
| [[DFF Latch]]                                                             | <ul><li>#status/finished</li></ul> |
| [[HardwareSimulator]]                                             | <ul><li>#status/finished</li></ul> |
| [[SR Latch temporizzato]]                                     | <ul><li>#status/finished</li></ul> |
| [[Cache]]                                                                     | <ul><li>#status/finished</li></ul> |
| [[Virtual machine]]                                                 | <ul><li>#status/finished</li></ul> |
| [[Record di attivazione]]                                     | <ul><li>#status/finished</li></ul> |
| [[Codifica numeri interi]]                                   | <ul><li>#status/finished</li></ul> |
| [[Linking statico]]                                                 | <ul><li>#status/finished</li></ul> |
| [[NOT]]                                                                         | <ul><li>#status/finished</li></ul> |
<!-- SerializedQuery END -->

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=53548)
- [dynamik](https://dynamik.vercel.app/architettura-degli-elaboratori)