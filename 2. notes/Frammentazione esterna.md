---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
date: 24-11-2023 17:17:21
links:
  - "[[Lecture 20112023130829]]"
  - "[[Lecture 26022025111603]]"
---
# Frammentazione esterna
---
## Introduzione
> La **frammentazione esterna** è una [[Frammentazione|frammentazione]] della [[RAM]] che si verifica come conseguenza della [[Segmentazione|segmentazione]].

Lo _swap_ di un segmento dalla memoria secondaria a quella principale non avviene in maniera così banale come per la [[Paginazione|paginazione]]. Questo perché i segmenti hanno grandezze distinte. In particolare la frammentazione esterna si verifica quando **un blocco di una certa dimensione viene sostituito da uno di dimensione minore**, lasciando in memoria un piccolo _gap_ che non è riempibile con nessun altro segmento.

Questi gap, sparsi nella memoria, finiscono con l'accumularsi, portando ad una situazione di stallo, in cui _gli spazi rimasti non sono abbastanza grandi da contenere un nuovo segmento_.

Quindi, in una situazione di frammentazione esterna, _ci sarebbe complessivamente lo spazio necessario, ma e' inutilizzabile perche' suddiviso in porzioni di memoria contigua troppo piccole_.

<u>Nota bene</u>: il motivo per cui non possiamo pensare di spezzare il dato nelle porzioni non contigue di memoria, e' perche' **bisogna rispettare le modalita' e quindi i tempi di accesso alle variabili**. Si pensi a un [[Array|array]]: _dev'essere memorizzato in modo contiguo perché l'accesso dev'essere tramite un offset_; in realta' anche le stesse variabili non sono accedute tramite il nome, ma da un offset a partire dalla prima dichiarazione (come se fossero elementi di un array).

## Soluzione
Per risolvere, o almeno limitare il più possibile la frammentazione esterna, ci sono tre tecniche:
- [[Best fit|best fit]]
- [[First fit|first fit]]
- [[Defrag|defrag]]

Il metodo però migliore per evitare del tutto la frammentazione esterna consiste nel [[Combinazione segmentazione-paginazione|combinare la segmentazione con la paginazione]].

## Referenze