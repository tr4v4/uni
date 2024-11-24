---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 30-10-2024 21:30:45
links:
  - "[[Lecture 15102024091721]]"
  - "[[Lecture 22102024092339]]"
---
# Ottimizzazione di dati
---
## Introduzione
Una delle più importanti applicazioni dell'[[Algebra lineare|algebra lineare]] risiede nei problemi di ottimizzazione. Infatti, _tutti i problemi reali risolvibili computazionalmente possono essere in qualche modo riformulati come problemi di ottimizzazione_ (ad esempio la [[Ricerca operativa|ricerca operativa]]).

## Definizione
> L'**ottimizzazione di dati** è una branca della matematica che studia la soluzione di problemi riscrivibili nella forma
> $$\min_{x \in \Omega} f(x)$$
> In poche parole, _definito il dominio dei vincoli $\Omega$ e la funzione $f: \Omega \to \mathbb{R}$, si vuole trovare l'argomento $x \in \Omega$ che renda minimo $f(x)$_.

Un esempio è quello del [[Problema del commesso viaggiatore|problema del commesso viaggiatore]], modellizzabile matematicamente in:
$$\min_{x \in \Omega \subset \mathbb{R}^{n}} \sum\limits_{i=1}^{n-1} d(x_{i}, x_{i+1})$$

## Classificazione
I problemi di ottimizzazione di dati si possono classificano in tantissimi modi diversi, in base all'elemento analizzato.

### $\Omega$
Si classificano in base al dominio dei vincoli in:
- **unconstrained** (problema _svincolato_) $\iff \Omega = \mathbb{R}^{n}$
- **constrained** (problema _vincolato_) $\iff \Omega \subset \mathbb{R}^{n}$
	- **discrete** (problema _discreto_) $\iff \Omega \subseteq \mathbb{Z}^{n}$

### $f$
Si classificano in base alla funzione $f$ in due sotto-classificazioni.

#### Derivabilità
- **smooth** (almeno _derivabile_) $\iff f \in C^{1}(\Omega)$[^1]
- **non-smooth** (_non derivabile_) $\iff f \notin C^{1}(\Omega)$

<u>Nota bene</u>: i _non-smooth_ sono difficilissimi da risolvere.

#### Complessità
- **lineare** $\iff f(x) = x^{T}w$
- **quadratico** $\iff f(x) = x^{T}Ax + x^{T}b$[^2]

## Minimi
All'interno dell'ottimizzazione, i [[Massimo e minimo relativo|minimi locali e globali]] assumono un significato preciso: i **minimi locali rappresentano una soluzione buona solo localmente**, tale che _se cambiata di poco peggiora, ma se cambiata radicalmente migliora_. Purtroppo è computazionalmente inefficiente distinguere i locali dai globali, per cui solitamente ci si accontenta dei locali[^3].

Per poter lavorare allora in modo tale da garantirsi come soluzioni dei minimi globali, è necessario fare delle assunzioni su $f$. In particolare si richiede che:
- $f$ sia _[[Funzione convessa|convessa]]_;
- $f$ sia _[[Funzione coerciva|coerciva]]_.

Il motivo per cui ci interessano le funzioni convesse è che:
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$ convessa, allora _tutti i punti $x^{*}$ di minimo locale sono anche minimi globali_.

L'ipotesi della coercività, invece, è necessaria per il seguente teorema:
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$ coerciva, allora _esiste per $f$ almeno un minimo locale_.

Se si uniscono convessità e coercività, si ottiene che **esiste almeno un minimo, e che quel minimo è per forza globale**[^4].

### Condizioni
Elenchiamo dei risultati teorici che ci consentono di sviluppare degli algoritmi per la ricerca di questi minimi in modo sistematico:
- _condizione necessaria del primo ordine_ --> sul [[Gradiente|gradiente]]
	- definizione: un punto $x^{*}$ è stazionario se $\nabla f(x^{*}) = 0$
	- teorema: ogni punto di minimo di $f$ è un punto stazionario ([[Teorema di Fermat]])
	- è il teorema più debole
	- però se $f$ è convessa e coerciva, allora ogni soluzione di $\nabla f(x) = 0$ è un punto di minimo globale
- _condizione necessaria del secondo ordine_ --> sull'hessiana
	- teorema: se $x^{*}$ è minimo, allora $\nabla f(x^{*}) = 0$ e $H_{f}(x^{*})$ è semi-definita positiva, ovvero $x^{T}H_{f}(x^{*})x \geq 0 \ \ \ \forall x \in \mathbb{R}^{n}$
- _condizione sufficiente del secondo ordine_ --> sull'hessiana
	- teorema: se $x^{*}$ è stazionario e $H_{f}(x^{*})$ è definita positiva (non semi), allora $x^{*}$ è un punto di minimo di $f$
	- se noi sappiamo che, in quanto $f$ convessa, $H_{f}(x^{*})$ è sempre semi-definita positiva, quindi ogni soluzione $x^{*}$ del punto 1 è un punto di minimo tranne per quei punti per cui $H_{f}(x^{*})$ è singolare ([[Determinante|determinante]] diverso da 0)

## Algoritmi
Gli algoritmi che risolvono i problemi di ottimizzazione sono:
- [[Metodo di discesa del gradiente|metodo di discesa del gradiente]]

## Referenze
[^1]: [[Classe C|classe C]]
[^2]: il [[Problema dei minimi quadrati|problema dei minimi quadrati]] ricade in questa categoria!
[^3]: il problema di riconoscere, data una funzione, un suo minimo globale, è [[NP-Hard]]
[^4]: tutti i _problemi dei minimi quadrati sono convessi e coercivi_!