---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 18-02-2025 10:53:16
links:
  - "[[Lecture 17022025090125]]"
  - "[[Lecture 19022025091652]]"
---
# Problema di ottimizzazione
---
## Introduzione
> I **problemi di ottimizzazione** sono [[Problema|problemi]] in cui occorre sempre _massimizzare i ricavi e profitti_ o _minimizzare i costi e perdite_, in presenza di _risorse limitate_. Formalmente, si definisce una **funzione obiettivo** $$c_{\mathcal{P}}: \mathbb{F}_{\mathcal{P}} \to \mathbb{R}$$
> che misura il costo/beneficio della soluzione in $\mathbb{F}_{\mathcal{P}}$ (l'insieme delle soluzioni ammissibili), tale che:
> - il _problema di massimo $\mathcal{P}$_ consiste nel determinare il valore $$Z_{\mathcal{P}} = \max\{c_{\mathcal{P}}(g) | g \in \mathbb{F}_{\mathcal{P}}\}$$
> - il _problema di minimo $\mathcal{P}$_ consiste nel determinare il valore $$Z_{\mathcal{P}} = \min\{c_{\mathcal{P}}(g) | g \in \mathbb{F}_{\mathcal{P}}\}$$

<u>Nota bene</u>: ad ogni problema di massimo $\mathcal{P}$ ne corrisponde uno di minimo $\mathcal{P}'$ tale che $c_{\mathcal{P}'}(g) = -c_{\mathcal{P}}(g)$, infatti $$Z_{\mathcal{P}} = -\min\{c_{\mathcal{P}'}(g) | g \in \mathbb{F}_{\mathcal{P}} = \mathbb{F}_{\mathcal{P}'}\}$$

La [[Ricerca operativa|ricerca operativa]] e l'ottimizzazione combinatoria hanno come oggetto di studio le metodologie a supporto delle [[Processo decisionale|decisioni]].

### Notazione
E' importante distinguere tra _valore ottimo_ e _soluzione ottima_:
- dato $\mathcal{P}$, $Z_{\mathcal{P}}$ è detto **valore ottimo** per $\mathcal{P}$;
- dato $\mathcal{P}$, un $g^{*} \in \mathbb{F}_{\mathcal{P}}$ tale che $Z_{\mathcal{P}} = c_{\mathcal{P}}(g^{*})$ è detto **soluzione ottima**.

## Categorie
I problemi di ottimizzazione si dividono in:
1. **problema vuoto** --> $\mathbb{F}_{\mathcal{P}} = \varnothing$, e per convenzione $Z_{\mathcal{P}} = \infty$;
	- non è triviale rilevarlo (a volte nei problemi di ottimizzazione la difficolta' sta proprio nel rilevare se l'insieme delle soluzioni ammissibili è vuoto)
2. **problema illimitato** --> nel caso del problema di massimo, per ogni $x \in \mathbb{R}$ esiste sempre un $g \in \mathbb{F}_{\mathcal{P}}$ con $c_{\mathcal{P}}(g) \geq x$[^1]; di conseguenza $Z_{\mathcal{P}} = +\infty$;
	- duale nel caso del problema di minimo
3. **valore ottimo finito, ma non soluzione ottima finita** --> se si considera $\min\{x | x > 0\}$ il valore ottimo magari esiste ed è 0, ma la soluzione non è ben definibile (ti devi avvicinare allo 0 all'infinito);
	- dipende da come si definisce $\mathbb{F}_{\mathcal{P}}$, in particolare se e' un [[Insieme|insieme]] _topologicamente aperto_
4. **valore ottimo finito, e soluzione ottima finita** --> caso ottimale
	- <u>attenzione</u>: il valore ottimo è solo e solamente 1, ma le soluzioni ottime possono essere multiple

## Equivalenze
Esiste una relazione tra i problemi di ottimizzazione e i [[Problema di decisione|problemi di decisione]]. In modo particolare, fissato un problema $\mathcal{P}$, e' sempre possibile passare da una formalizzazione all'altra.

### Problema di decisione $\to$ problema di ottimizzazione
Dato un problema di decisione $\mathcal{P}$, e' sempre possibile vederlo come _il problema di ottimizzazione che come funzione obiettivo ha una funzione costante_.

Infatti, che si tratti di un problema di massimo o di minimo, _il massimo o minimo di una funzione costante uniforma l'insieme delle soluzioni ammissibili $\mathbb{F}_{\mathcal{P}}$_, rendendo il problema di ottimizzazione un problema di decisione.

### Problema di ottimizzazione $\to$ problema di decisione
Dato un problema di ottimizzazione $\mathcal{P}$, allora posso vederlo come un problema di decisione $\mathcal{R}$ lavorando sull'insieme delle soluzioni ammissibili $\mathbb{F}_{\mathcal{R}}$, in 2 modi possibili:
- $$\mathbb{F}_{\mathcal{R}} = \{g \in \mathbb{F}_{\mathcal{P}} | c_{\mathcal{P}}(g) = Z_{\mathcal{P}}\}$$
- considerando $k \in \mathbb{R}$ $$\mathbb{F}_{\mathcal{R}_{k}} = \{g \in \mathbb{F}_{\mathcal{P}} | c_{\mathcal{P}}(g) \leq k\}$$ (considerando $\mathcal{P}$ problema di minimo)

L'idea di quest'ultimo approccio e' di definire un bound $k$ su cui trovare la soluzione (nel problema di decisione associato), perche' la soluzione ottima del problema di ottimizzazione sarebbe troppo costosa da calcolare.

## Algoritmi
Esistono 2 categorie di algoritmi per risolvere i problemi di ottimizzazione:
- [[Algoritmo esatto|algoritmi esatti]];
- [[Algoritmo euristico|algoritmi euristici]].

## Referenze
- [[Problema di decisione]]
- [[Problema di certificato]]

[^1]: proprio la definizione di [[Limite di funzione|limite]]