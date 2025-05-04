---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 18:36:36
links:
  - "[[Lecture 06032025151956]]"
---
# PCB
---
## Introduzione
> Un **PCB** (**Process Control Block**) e' una [[Strutture dati|struttura dati]] contenente le informazioni che identificano un [[Processo|processo]], in particolare:
> - _identificazione del processo_
> 	- `pid`, che potrebbe essere l'indice dell'array della tabella, ma questo causerebbe il problema della reincarnazione, quindi e' un numero progressivo;
> 	- identificatore del padre, o di processi correlati;
> 	- identificatore dell'utente che ha richiesto la sua esecuzione;
> - _stato del processo_
> 	- [[Registro#Registri generali|registri generali]] del [[CPU|processore]];
> 	- [[Registro#Registri speciali|registri speciali]] del processore ([[PC]] e [[PSW]]);
> 	- informazioni di [[Scheduling|scheduling]] varie;
> - _controllo del processo_
> 	- stato del processo;
> 	- [[Gestione della memoria|gestione della memoria]];
> 	- accounting (importanti per misurare le prestazioni!);
> 	- relative alle risorse;
> 	- priorita' (per le politiche di scheduling);
> 	- interprocess comunication ([[IPC]]);

## Referenze