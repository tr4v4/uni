---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 19:13:59
links:
  - "[[Lecture 19032025113725]]"
---
# Eccezione
---
## Introduzione
> Un'**eccezione** è un evento che si verifica durante l'esecuzione di un programma e che interrompe il normale flusso di istruzioni. Si tratta a tutti gli effetti di un costrutto di programmazione, che consente di gestire in modo elegante gli errori e le situazioni impreviste, nonche' di migliorare l'efficienza di esecuzione del programma stesso.

## Concetti
![[eccezione-esempio.png]]

### Gestore
Il gestore dell'eccezione e' legato in modo statico al blocco di codice protetto, cosi' _quando viene eseguito rimpiazza la parte di blocco che doveva essere ancora eseguita_.

### Propagazione
Se l'eccezione non e' gestita nella routine corrente, viene propagata al chiamante; se a sua volta non e' gestita dal chiamante, viene propagata al chiamante del chiamante, risalendo di fatto la [[Catena dinamica|catena dinamica]]. Alla fine, se non viene gestita da nessuno, si raggiunge il top-level, ovvero il sistema operativo, che si occupa di gestirla in modo generico.

Ad ogni livello della catena dinamica che propaga l'eccezione, viene tolto il suo [[Record di attivazione|record di attivazione]] e ripristinati i registri.

### Implementazione
#### Naive
Possiamo pensare di usare una [[Pila|pila]] in cui andare a inserire i gestori ogni volta che si entra in un `try`: quando c'e' un'eccezione si toglie dalla pila il gestore, e se non e' quello giusto risollevi l'eccezione e si continua a togliere dalla pila finche' non troviamo il gestore giusto.

Non e' il massimo perche' abbiamo un overhead di tempo e spazio.

#### Migliore
- il compilatore genera una tabella dove, per ogni blocco protetto e per ogni routine, c’è una coppia `<block_addr, handler_addr>`
- la tabella è ordinata sul primo elemento (staticamente)
- al sollevamento di un’eccezione:
	- ricerca binaria nella tabella del ProgCounter sul primo elemento
	- trasferimento del controllo all’indirizzo corrispondente del gestore
- se il gestore risolleva l’eccezione, ripeti
- attenzione: se il gestore è quello nascosto di una routine la prossima ricerca nella tabella deve avvenire non col PC, ma con l’indirizzo di ritorno della routine

## Referenze