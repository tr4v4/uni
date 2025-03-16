---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 16:30:26
links:
  - "[[Lecture 21022025091223]]"
---
# Protezione hardware
---
## Introduzione
> I [[Sistema operativo|sistemi operativi]] [[Multiprogramming|multiprogrammati]] e multiutente richiedono la presenza di meccanismi di **protezione hardware**. In particolare, _bisogna evitare che i processi utente interferiscano con il sistema operativo_.

Meccanismi di questo tipo non possono essere realizzati con il solo software: **serve l'hardware**.

## Modalita'
Solitamente le due modalita' previste sono _utente_ e _kernel_.

### Modalita' utente
I [[Processo|processi]] eseguiti in modalita' utente non hanno accesso alle istruzioni privilegiate, come per esempio quella per [[Disabilitazione degli interrupt|disabilitare gli interrupt]].

### Modalita' kernel / supervisore / privilegiata / ring 0
I processi in modalita' kernel hanno accesso a tutte le istruzioni, incluse quelle privilegiate che gli consentono di gestire totalmente il sistema.

Tutte le istruzioni di [[I-O]] sono da considerarsi privilegiate. Di fatto, il [[Sistema operativo|sistema operativo]] dovra' fornire agli utenti delle primitive ([[System call|system call]]) per accedere all'I-O.

<u>Nota bene</u>: infatti **le system call NON sono istruzioni privilegiate**! Ogni processo puo' chiamarle, e questo generera' una [[Trap|trap]] che da' il via al codice del sistema operativo che e' in modalita' kernel, per cui puo' eseguire le istruzioni di I-O.

## Implementazione
Le due modalita' sono segnalate dal valore del **mode bit**, _1 singolo bit che indica la modalita' corrente della CPU_ (nel [[PSW]], [[Registro|registro]] di stato).

La protezione deve avvenire anche a lato [[Memorie|memoria]]: attraverso la [[MMU]]. Altrimenti i processi utente potrebbero:
- modificare il codice o i dati di altri processi utenti;
- modificare il codice o i dati del sistema operativo;
- modificare l'[[Interrupt vector|interrupt vector]], inserendo i propri [[Interrupt handler|gestori degli interrupt]].

## Funzionamento
Come funziona il passaggio tra queste modalita'?

Si seguono i seguenti passaggi:
- alla partenza il processore e' in modalita' kernel;
- viene caricato il sistema operativo ([[Bootstrap|bootstrap]]) e si inizia ad eseguirlo;
- quando questo cede il controllo a un processo utente, prima di farlo cambia il valore del _mode bit_ ponendo il processore in modalita' utente;
- tutte le volte che avviene un [[Interrupt|interrupt]] (sia hardware che software), si passa alla modalita' kernel --> [[Mode switch|mode switch]];

## Referenze