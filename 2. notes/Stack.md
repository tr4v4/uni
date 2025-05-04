---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
date: 05-11-2023 19:28:23
links:
  - "[[Lecture 03112023110813]]"
  - "[[Lecture 20022025131602]]"
---
# Stack
---
## Definizione
> Lo **stack** è quella parte di [[Allocazione dinamica della memoria dei programmi|memoria]] riservata a un [[Processo|processo]] in esecuzione in cui vengono _allocati i [[Record di attivazione|record di attivazione]]_ delle [[Funzione informatica|funzioni]].

E' una memoria di tipo [[LIFO]]. Ha un [[Registro|registro]] dedicato chiamato _Stack Pointer_ ([[SP]]).

## Funzionamento
La gestione della pila avviene in 4 steps:
1. **sequenza di chiamata** --> eseguito dal chiamante immediatamente prima della chiamata;
2. **prologo** --> eseguito all'inizio del blocco;
3. **epilogo** --> eseguito alla fine del blocco;
4. **sequenza di ritorno** --> eseguito dal chiamante immediatamente dopo la chiamata;

In particolare _chiamata_ e _prologo_:
- modificano il [[PC]]
- allocano l'RdA sulla pila, e modificano puntatore a top ([[SP]])
- modificano il puntatore all'RdA
- fanno il passaggio dei parametri
- salvano i registri
- fanno eventuali inizializzazioni
- trasferiscono il controllo

Invece _epilogo_ e _ritorno_:
- restituiscono i valori dal chiamato al chiamante, oppure il valore calcolato dalla funzione
- ripristinano i registri, in particolare deve essere ripristinato il vecchio valore del puntatore al RdA
- fanno eventuale finalizzazione
- deallocano lo spazio sulla pila
- ripristinano il valore del PC

## Referenze