---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 13:56:16
links:
  - "[[Lecture 16112023133640]]"
---
# SO
---
## Introduzione
Un computer contiene una _serie di [[Architettura di von Neumann#Introduzione|risorse hardware]] che possono eseguire dei programmi software_. E' possibile, per esempio, caricare manualmente in [[RAM]] un programma, farlo eseguire alla [[CPU]] e ottenere un risultato salvato in [[Memorie#Classificazione|memoria di massa]]. Ovviamente è un modo scomodo per eseguire programmi, ed è limitato per esempio nell'esecuzione di un singolo programma alla volta.

La soluzione che si propone è allora quello di _far eseguire al computer un unico generico software che consente di eseguire programmi e che gestisca l'hardware sottostante_: il **sistema operativo**.

Questo farebbe del sistema operativo l'**interfaccia vera e propria tra il calcolatore e i programmi applicativi**: questi, in particolare, interagirebbero con l'hardware attraverso delle [[System call|system call]]...

### Struttura
![[struttura-sistema-operativo-unix.png]]

## Compiti
Di fatto il sistema operativo si occupa di:
- _gestire la memoria_
	- [[Paginazione|paginazione]]
	- [[Segmentazione|segmentazione]] (ed eventuale [[Combinazione segmentazione-paginazione|combinazione]])
- _gestire i [[Processo|processi]]_
- _gestire le periferiche [[I-O|I/O]]_

Sono compiti estremamente complessi...

## Referenze