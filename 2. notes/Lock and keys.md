---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2025 19:12:35
links:
  - "[[Lecture 30042025110449]]"
---
# Lock and keys
---
## Introduzione
> Per **lock and keys** si intende una _tecnica usata per gestire i [[Dangling pointer|dangling pointers]]_.

Sono un'alternativa alle [[Tombstones|tombstones]], ma solo per la gestione dell'[[Heap|heap]].

## Funzionamento
Di base, ogni volta che [[Allocazione|allochiamo]] un oggetto sull'heap, lo associamo a un _lock_, costituito da una _word casuale_ in memoria.
Un puntatore a quell'oggetto allocato, allora consistera' nella coppia:
- indirizzo effettivo;
- word dell'oggetto allocato, detta _key_.

Semplicemente, ogni volta che si dereferenzia un puntatore, **si controlla che la chiave possa aprire il lucchetto**! Ovvero che le due word coincidano.

Quando assegnamo allora un puntatore al valore di un altro, questo copiera' sia l'indirizzo che la key.

Al momento della deallocazione, _cancelliamo l'oggetto dalla memoria e impostiamo il valore del suo lock su un valore canonico_ (non appartenente al dominio delle chiavi): in questo modo invalidiamo ogni possibile dereferenziazione successiva.

### Esempio
```C
{
	char *dp = NULL;
	{
		char c = "a";
		dp = &c;
	}
}
```
![[lock-and-keys.png]]

### Osservazioni
Potrebbe capitare, che un lock precedentemente deallocato venga usato come nuovo lock: in tal caso **c'e' il rischio che un dangling pointer abbia la chiave identica al nuovo valore del lock**. Ma e' bassissimo!

## Problemi
Costano anche di piu' delle tombstones: c'e' bisogno di _un'intera word per ogni puntatore_.

Inoltre, in termini di tempo, costa la creazione, l'assegnamento e la dereferenziazione (si esegue sempre un controllo di equivalenza).

## Referenze