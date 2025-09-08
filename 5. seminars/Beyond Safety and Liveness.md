---
tags:
  - category/seminar
date: 02-09-2025 16:28:19
lecturer: Fred B. Schneider
---
# Beyond Safety and Liveness
## Concetti
- formal methods per verificare la **correttezza dei programmi**
	- chiaramente Turing ha introdotto l'idea con un articolo
	- negli anni '60:
		- correzione parziale --> se il programma termina allora termina correttamente
		- correzione totale --> il programma termina e termina correttamente
	- negli anni '70:
		- "la correttezza è negli occhi di chi osserva"
		- quindi la correttezza diventa se il programma soddisfa delle specifiche
		- esempio con la mutua esclusione
	- definizioni
		- behavior - sequenza di stati $\sigma: s_{0}s_{1}\cdots s_{i}\cdots$
		- i behavior sono infiniti
		- Program $S$, insieme di behaviors $\{\sigma | \hat{S}(\sigma)\}$
		- Property $P$, insieme di behaviors $\{\sigma | \hat{P}(\sigma)\}$
		- $S$ soddisfa $P$ significa che ne è un sottoinsieme
	- safety e liveness formalizzati
	- teoremi
		- ogni proprietà è la congiunzione di una proprietà safety e di una proprietà liveness --> sono una base! (algebra lineare)
		- dato un sistema
			- verificare la safety richiede di provare l'_invarianza_
			- verificare la liveness richiede di provare la _ben-fondatezza_
		- questa diventa la base per provare ogni proprietà di ogni programma!
	- ma le proprietà non sono sufficienti...
		- non possono relazionare relazioni multiple
	- allora lui ha introdotto le **hyperproperties**
		- è un predicato su un insieme di proprietà
		- ha dimostrato che queste raggiungono la massima espressività (non esistono hyperhyperproperties)
		- teoremi
			- ogni iperproprietà è la congiunzione di una safety iperproprietà e di una liveness iperproprietà (stesso teorema di prima)
		- la verifica di iperproprietà è diventata è una branca, che ha richiesto di inventare una nuova logica e nuovi metodi
			- in realtà si possono usare anche la logica standard, insomma niente di nuovo

## Domande

## Referenze