---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-10-2024 16:58:39
links:
  - "[[Lecture 10102024092110]]"
  - "[[Lecture 17102024091631]]"
---
# Processo
---
## Introduzione
> Per **processo** si intende un'attività controllata da un programma che si svolge su un [[CPU|processore]].

### Processo vs. programma
Un **processo non è un [[Programma|programma]]**:
- un programma è un'_entità statica_, che specifica una sequenza di istruzioni (e non la durata nel tempo dell'esecuzione);
- un processo è un'_entità dinamica_, che rappresenta l'attività dell'esecuzione di un programma.

## Caratteristiche
Una delle proprietà fondamentali dei processi è descritta da un'[[Assioma|assioma]]: l'[[Assioma di finite progress|assioma di finite progress]].

Più processi possono eseguire lo stesso programma: ogni istanza viene considerata un processo separato. Nel dettaglio, si condivide la parte di memoria riservata al codice del programma (`TEXT`), mentre le parti private delle singole istanze non sono condivise (`DATA` e `STACK`).

## Stato
Ad ogni istante un processo è descritto da:
1. _la sua immagine in [[RAM|memoria]]_ (la memoria assegnata e le strutture dati del sistema operativo associate al processo);
2. _la sua immagine nel processore_ (contenuto dei [[Registro|registri]] [[Registro#Registri generali|generali]] e [[Registro#Registri speciali|speciali]]);
3. _lo stato di avanzamento_ (il suo stato corrente, se è in esecuzione o in attesa di qualche evento).

Un processo si può trovare in 3 stati:
- **running** - processo in esecuzione;
- **waiting** - processo in attesa di qualche evento esterno;
- **ready** - processo pronto per essere eseguito, in attesa del via dal processore;

![[stati-processo.png]]

## Interazioni
### Processi
I processi si classificano in base a quanto sono consapevoli gli uni degli altri:
- _processi indipendenti_;
- _processi in conoscenza indiretta_;
- _processi in conoscenza diretta_;

#### Processi indipendenti
Sono totalmente ignari gli uni degli altri, per cui _competono per le stesse risorse e devono sincronizzarsi nel loro utilizzo_.

Dev'essere proprio il _[[Sistema operativo|sistema operativo]] ad arbitrare competizione e sincronizzazione_.

#### Processi in conoscenza indiretta
Condividono delle risorse al fine di scambiarsi informazioni, per cui _non si conoscono perfettamente ma interagiscono indirettamente attraverso di esse_. Devono _cooperare per qualche scopo e sincronizzarsi nell'utilizzo delle risorse_.

In questo caso il _sistema operativo deve facilitare la cooperazione fornendo meccanismi di sincronizzazione_.

#### Processi in conoscenza diretta
Questi comunicano uno con l'altro sulla base dei loro _id_, praticamente una comunicazione diretta basata sullo scambio di messaggi. _Cooperano per qualche scopo e comunicare informazioni agli altri processi_.

Qui il _sistema operativo deve facilitare la cooperazione fornendo meccanismi di comunicazione_.

### Modelli
I processi interagiscono su due modelli di utilizzo della memoria:
- **memoria condivisa** - comunicazione tramite sincronizzazione;
- **memoria privata** - sincronizzazione tramite comunicazione;

## Referenze