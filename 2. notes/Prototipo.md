---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2025 17:58:50
links:
  - "[[Lecture 08052025131742]]"
---
# Prototipo
---
## Introduzione
> I **prototipi** sono un'_alternativa alle [[Classe|classi]] per la creazione degli [[Oggetto|oggetti]]_.

Si chiama anche **delegazione**: si basa sulla _possibilita' che degli oggetti deleghino parti della loro implementazione ad altri oggetti_.

## Funzionamento
Gli oggetti possono delegare la definizione di valori e metodi a un altro oggetto, tramite la loro proprieta' (campo) **prototipo**.

In [[JS]], per esempio, definisco un oggetto e i suoi attributi cosi':
```js
function Counter() {
	this.x = 1;
}

Counter.prototype.get = function() {
	return this.x;
}
Counter.prototype.inc = function(i) {
	this.x += i;
}
```

<u>Nota bene</u>: si', `Counter` e' un oggetto perche' in javascript ogni cosa e' un oggetto[^1]...

A questo punto, per creare un nuovo oggetto di tipo Counter posso fare:
- **ex-nihilo** - non assegna alcun prototipo al nuovo oggetto;
- **clonazione** - crea il nuovo oggetto facendo una copia del prototipo dell'oggetto dopo la keyword `new`;

Per esempio
```js
c = new Counter();
```
crea un nuovo oggetto `c` che copia dall'oggetto `Counter` il suo prototipo. Quindi il prototipo di `c` adesso sara' uguale a quello di `Counter`.

## Differenza con classi
Funzionalmente i prototipi fungono anch'essi da modelli per creare altri oggetti, **linguisticamente sono oggetti stessi, eventualmente usati come modelli**!

I prototipi possono formare una rete di gerarchia di "scarico delle responsabilita'". Fondamentalmente **se un oggetto non trova un campo o un metodo invocato, lo delega al suo delegato** (il prototipo). A sua volta, se questo non lo trova, lo delega al suo prototipo, e cosi' via fino ad arrivare, nel caso, al prototipo vuoto.

Di solito i casi in cui un prototipo ha un suo prototipo, avvengono per implementare l'[[Ereditarietà|ereditarieta']].

Un'altra importantissima differenza e' la possibilita', con i prototipi, di **cambiare il suo delegato a run-time**.

## Referenze

[^1]: e' proto [[Linguaggio di programmazione funzionale|funzionale]]
