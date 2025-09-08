---
tags:
  - category/seminar
date: 02-09-2025 17:48:57
lecturer: Nicola Prezza
---
# Algorithms, Data Structures, and Nucleotides
## Concetti
- DNA sequencing, assembling, alignment
	- sequencing --> spezzare il DNA in frammenti salvati in file come stringhe di A,C,G,T chiamati reads
	- (genome) assembling --> ricostruisci l'intero genoma (3 miliardi di lettere) a partire dai frammenti (reads)
		- è NP-completo, in oltre ci sono errori e ripetizioni
		- nel caso semplice in cui tutti questi problemi non ci sono, il problema diventa semplice
			- grafo di De Bruijn
	- alignment --> serve per verificare se ci sono delle varianti nel DNA di pazienti
		- vogliamo comprimere i file però di confronto, perché sono tantissimi
		- e vogliamo mantenerli compressi durante l'analisi!
			- si può fare usando la magia delle compact data structures
- DNA computing
	- salvataggio file
		- converti binario in quaternario, usando tecniche di correzione degli errori (la sintesi non è perfetta)
		- e poi fai la sintesi su molecole
		- al contrario per riottenere i dati
	- computazione
		- puoi trovare i cicli Hamiltoniani
		- è fottutamente Turing-completo

## Domande

## Referenze