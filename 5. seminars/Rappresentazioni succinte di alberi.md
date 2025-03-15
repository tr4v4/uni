---
tags:
  - category/seminar
  - topic/algoritmi-e-strutture-dati
date: 16-02-2025 09:31:57
lecturer: Giovanni Manzini
---
# Rappresentazioni succinte di alberi
## Concetti
- un albero di $n$ nodi occupa $\Theta(n \log{n})$ bits, sotto assunzioni standard
- il numero di alberi di $n$ nodi è dato dall'$n$-esimo numero di Catalan
	- per esempio con $n = 10$, ho $C_{10} = 16796$ alberi
	- ci si può mettere d'accordo nel seguente modo: sia mittente che destinatario conoscono tutti i 16796 alberi; il mittente comunica i 15 bit necessari per identificare lo specifico albero!
		- $\lceil \log_{2}(C_{10}) \rceil = 15$ bits
- si risparmia tantissimo se si identificano gli alberi in questo modo
- asintoticamente, in questo modo si ha che per rappresentare un albero di $n$ nodi bastano 2n bits: pochissimi
- ora, fare la lista di tutti gli alberi è poco pratico, ma se si aggiungono un po' di bit in più consentono di usare direttamente l'albero con 2n bits e di navigarlo in modo efficiente
	- si può sapere in tempo costante il numero di nodi di un sottoalbero
- rappresentazioni succinte:
	- **LOUDS**, rappresentazione per livelli + operazioni _rank_ e _select_ (e `poprank`) per navigare in tempo costante nell'albero
	- **Munro-Raman BP**, rappresentazione con parentesi bilanciate (usa DFS) + operazioni _findclose_ e _select_, consente di sapere in tempo costante il numero di nodi di un sottoalbero
	- **DFUDS**, combinazione delle precedenti, la migliore
	- **labeled tree**, per alberi che hanno delle label per ogni nodi, si vogliono delle operazioni per cercare dei nodi
- messaggio: _forse non è solo fortuna che comprimendo dei dati si ottenga una struttura con la stessa potenza espressiva e che consente anche di fare operazioni in più in tempo minore (costante)_!
- libri: Compact Data Structures - A practical approach, Gonzalo Navarro

## Domande

## Referenze