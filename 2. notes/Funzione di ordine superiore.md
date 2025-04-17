---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 18:06:47
links:
  - "[[Lecture 12032025111631]]"
  - "[[Lecture 19032025113725]]"
---
# Funzione di ordine superiore
---
## Introduzione
> Le **funzioni di ordine superiore** sono [[Funzione informatica|funzioni]] che _consentono di prendere altre funzioni come parametri e di restituire funzioni come valore di ritorno_.

## Problemi
### Passaggio di funzione
Nel momento in cui una funzione viene passata come parametro, e' _necessario stabilire quale [[Ambiente|ambiente]] non locale si applica al momento della sua esecuzione_.

Prendiamo come esempio il seguente caso:
```C
int x=4;
int z=0;
int f(int y) {
	return x*y;
}

void g(int h(int n)) {
	int x;
	x = 7;
	z = h(3) + x;
}

{
	int x = 5;
	g(f);
}
```

Se assumiamo di essere in [[Scope statico|scope statico]], allora siamo certi del fatto che la `x` di `f` verra' valutata nell'ambiente globale, per cui sara' uguale a `4`.

Se invece usiamo [[Scope dinamico|scope dinamico]], quella `x` potrebbe essere risolta:
- `5` se si prende come riferimento l'ambiente al momento del passaggio;
- `7` se si prende come riferimento l'ambiente al momento dell'invocazione.

I due casi sono rispettivamente detti:
- [[Deep binding|deep binding]];
- [[Shallow binding|shallow binding]].

Entrambi questi due meccanismi sono implementati mediante la [[Chiusura|chiusura]].

#### Scope statico
Si potrebbe concludere erroneamente che nel caso di scope statico, tra deep e shallow binding non ci sia differenza. In realta', in funzioni ricorsive puo' capitare che ci sia differenza tra le due:
![[scope-statico-deep-shallow.png]]

In questo caso, la valutazione dell'`x` ritornato da `fie` viene sempre valutata staticamente come la `x` di `foo`, ma essendo `foo` ricorsiva e' la scelta tra deep e shallow binding che fa cambiare il valore di `x`!

Infatti, se si e' in deep binding, la `x` presa e' 1; se si e' in shallow e' invece `0`.

<u>Nota bene</u>: in questo specifico caso, tra l'altro, la stessa identica differenza si avrebbe con lo scope dinamico, perche' `x` e' immediatamente risolvibile tra i parametri formali di `foo`, e cio' che determina "da quale `foo`" (record di attivazione) andare a risolverla e' compito del tipo di binding.

### Restituzione di funzione
![[funzioni-ordine-superiore-restituzione1.png]]

In questo caso, non c'e' alcun problema: la `x` a cui fa riferimento `g` e' "sempre disponibile" al di fuori di `F`.

Ma nel momento in cui `x` diventa interna ad `F`
![[funzioni-ordine-superiore-restituzione2.png]]
ecco che si presenta il problema principale della restituzione di una funzione: la variabile (`x`) sparisce una volta che la funzione viene terminata, per cui la funzione restituita (`g`) accedera' a una locazione inesistente o sbagliata, di un [[Record di attivazione|record di attivazione]] tolto dallo [[Stack|stack]]!

Per far sopravvivere la variabile interna **si memorizza il record di attivazione della funzione "generatrice" sull'[[Heap|heap]]**.

## Referenze