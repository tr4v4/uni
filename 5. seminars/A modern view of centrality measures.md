---
tags:
  - category/seminar
date: 15-02-2025 09:34:52
lecturer: Paolo Boldi
---
# A modern view of centrality measures
## Concetti
- ricerca sui grafi per stabilire nodi _rilevanti_
	- ma cosa significa rilevante? come si misure l'importanza?
	- cosa vuol dire aumentare la propria importanza?
- indice:
	- centralità
	- assiomatica
	- caso orientato
	- caso non-orientato
- **centralità**
	- $c_{G}: V_{G} \to \mathbb{R}$
	- una funzione che ad ogni nodo di un grafo assegna un valore di importanza
	- misure esempio:
		- su Instagram, per esempio, il numero di follower è un indice di centralità
		- quindi, il numero di vicini, in particolare di in-vicini (archi entranti)
		- anche le elezioni di un sindaco funzionano così
		- questa misura si chiama _In-degree Centrality_
		- altra misura, calcoli la distanza media di un nodo da tutti gli altri (sempre archi entranti, nel caso di grafi orientati)
		- questa misura si chiama _Closeness Centrality_
	- la centralità nasce nelle scienze sociali
		- nato il concetto di "closeness", perfino storici hanno usato questa misura per comprendere il motivo dell'influenza dei Medici nel Rinascimento
		- è grazie ai motori di ricerca che la centralità è passata all'informatica
	- nota bene: useremo grafi orientati
	- centralità (misure):
		- _Path-based centralities_, basate sui cammini
			- _Betweenness_
			- _Katz_
		- _Spectral centralities_, basate sugli autovettori
			- _Eigenvector_
			- _Seeley index_
			- _PageRank_, quella di Google!
		- _Geometric centralities_
			- _Closeness_
			- _Harmonic_
	- algoritmi per la centralità: si vogliono trovare algoritmi efficienti per calcolare misure di centralità
	- senso della centralità: si studia il senso delle misure di centralità, per capire il loro significato
		- si fa usando un grafo _ground truth_, di cui si conosce la reale importanza dei nodi
		- oppure con un approccio _assiomatico_
- **assiomatica**
	- si pongono degli assiomi e si verifica per ogni misura di centralità se vengono o non vengono soddisfatti
- **caso diretto**
	- usiamo l'assioma di monotonia
		- se al grafo si aggiunge un follower di un nodo, il nodo in questione aumenta di importanza
		- si chiama _monotonia di punteggio_, alcune misure non lo soddisfano!
		- oppure la _monotonia del rank_:
			- se al grafo si aggiunge un follower di un nodo, il nodo in questione diventa non meno popolare (importante) di tutti gli altri nodi
		- considerazioni sui grafi non orientati, cosa succede alle due monotonie
			- caso orientato e non orientato cambiano tutto!
			- caso interessante di esempio, grafo di Hollywood
				- page rank in grafo non orientato, se un attore sconosciuto recita con uno famoso, quello famoso ci guadagna in popolarità mentre lo sconosciuto ci perde!
				- _Matthew effect_[^1]

## Domande

## Referenze
[^1]: https://en.wikipedia.org/wiki/Matthew_effect