---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2025 13:07:12
links:
  - "[[Lecture 30042025110449]]"
---
# Borrow-checking
---
## Introduzione
> Il **borrow-checking** e' un meccanismo di protezione della memoria, implementato per esempio in [[Rust]], che funziona limitando il modo in cui si possono utilizzare i [[Puntatore|puntatori]].

Un programma scritto in un linguaggio che implementa borrow-checking, se viene [[Compilatore|compilato]], allora e':
- privo di [[Dangling pointer|puntatori dangling]] e puntatori wild;
- privo di _double free_;
- privo di altri errori simili.

## Tecnica
L'idea si basa sulla proprieta' di **ownership**: ogni valore del programma ha un unico **owner** che ne determina la **lifetime** in memoria[^1].

### Ownership base
Per esempio, guardiamo questo codice:
```Rust
struct Person { name: String, birth: i32 }
let mut marx = Vec::new();
marx.push(Person { name: "Chico".to_string() , birth: 1887 });
marx.push(Person { name: "Harpo".to_string() , birth: 1888 });
marx.push(Person { name: "Groucho".to_string(), birth: 1890 });
marx.push(Person { name: "Gummo".to_string() , birth: 1893 });
marx.push(Person { name: "Zeppo".to_string() , birth: 1901 });
```

In memoria, avremo una situazione del tipo:
![[borrow-checking-1.png]]

In questo caso, quindi, l'array `marx` e' l'owner di oggetti `Person`, che a loro volta sono l'owner di oggetti `String`. Quando _`marx` esce dallo scope_, il borrow-checker sa che e' sicuro rimuoverlo dallo [[Stack|stack]] insieme a tutti gli oggetti dell'[[Heap|heap]] che possiede.

Per ora e' tutto molto semplice: _si tratta semplicemente di un albero, a cui se viene deallocata la radice viene automaticamente deallocato ogni suo nodo_.

### Ownership estesa
La reale ownership implementata, per esempio, da Rust, e' piu' complessa, e prevede:
- la **move** della ownership da un proprietario ad un altro;
- l'introduzione di **tipi speciali di puntatore con conteggio dei riferimenti** nel [[Sistema di tipi|sistema di tipi]];
- la **borrow** di un riferimento;

#### Move
E' letteralmente l'operazione di base fatta da Rust per:
- _assegnare un valore_ a una variabile;
- _passare un valore_ a una funzione;
- _restituire un valore_ da una funzione;

In altri linguaggi si fa la copia, mentre **in Rust viene spostata la proprieta' del valore**.

Per esempio, il seguente programma non compila in Rust:
```Rust
let s = vec![ “udon”, “ramen”, “soba” ];
let t = s;
let u = s;
```

Perche' dalla seconda assegnazione, _la proprieta' del valore di `s` viene spostata a `t` (non copiata!), e quindi `s` diventa vuoto_!
![[move-rust.png]]

Il principio si estende ai flussi di controllo (`if`):
```Rust
let x = vec![10, 20, 30];

if false { let a = x; }
else { let c = 2; }

let c = x;
```

Qui Rust non compila! Infatti, anche se non si entra mai nel ramo in cui la proprieta' del valore di `x` viene spostata ad `a`, Rust e' rigido e lo considera un caso possibile $\implies$ _la variabile `x` dopo l'`if` viene comunque considerata come non inizializzata_.

Il caso dei vettori indicizzati e' particolare. Teoricamente, _vorremmo poterci segnare che le celle da cui e' stato fatto un assegnamento_ (spostata la proprieta' di ownership) _non siano piu' inizializzate_. Nell'esempio:
```Rust
let v = vec!["a".to_string()];
let first = v[0];
```
vorremmo segnarci che `v[0]` non sia piu' inizializzata.

Tuttavia, a meno che gli indici non siano delle costanti, **non e' sempre possibile farlo a compile-time**! Si intendono tutti i _casi in cui gli indici sono delle espressioni_.

Percio' _non si ammette in Rust lo spostamento della ownership dalle collezioni_, ma **solo il riferimento o la copia**.

#### Conteggio dei riferimenti
A volte si vuole **condividere la proprieta' dei valori tra un insieme di owner**. Per questi casi Rust introduce i tipi `Rc` (_Reference Count_) e `Arc` (_Atomic Reference Count_)[^2].

Questi tipi _tengono traccia del numero di riferimenti a un valore per determinare se il valore e' ancora in uso o meno_. Se ci sono 0 riferimenti, il valore puo' essere rimosso.
```Rust
let s: Rc = Rc::new("a".to_string());
let t: Rc = s.clone();
let u: Rc = s.clone();
```

![[rc-arc-rust.png]]

Questo sistema _ricorda molto il sistema di [[Reference count|reference count]] come [[Garbage collector|garbage collector]]_. Da questo capiamo il grande limite: l'**impossibilita' di deallocare strutture ricorsive**.

Questi casi sono controllati e limitati da Rust, che infatti forza l'immutabilita' dei referenti di puntatori `Rc`. Nei casi in cui pero' servono davvero strutture cicliche, Rust consente di usare le _Reference Cells_, che sono _come gli `Rc` ma con i riferimenti mutabili_: questo si paga con controlli statici saltati, ed eventuali errori a run-time.

#### Borrow
I puntatori di tipo _owners_, quindi, quando sono rimossi, implicano la rimozione del valore riferito. Ma in Rust ci sono anche puntatori non proprietari: i _riferimenti_, che **al contrario degli owners dipendono dai loro riferiti**!
Il mantra e':
> I riferimenti non devono mai sopravvivere ai loro riferiti.

Questo evita facilmente dangling pointers: se il proprietario di un valore scompare, scompare anche il valore; e _qualora ci dovesse essere un riferimento a quel valore, deve scomparire anch'esso per evitare che diventi dangling_!

Per questo motivo, la **creazione di un riferimento a un valore si chiama borrowing**. Il riferimento da' accesso al valore senza modificarne la proprieta' di ownership. Puo' essere di 2 tipi:
- _riferimenti condivisi_ - consentono di leggere ma non di modificare il valore;
- _riferimenti mutabili_ - consentono di leggere e di modificare il valore, ma rendono impossibile avere altri riferimenti attivi a quel valore allo stesso tempo[^3].

I riferimenti non sono mai `NULL`. Il compilatore si occupa di controllare che le variabili non vengano mai utilizzate prima di essere inizializzate (puntatori wild).

##### Lifetimes
Per rispettare il mantra, entra in gioco il controllo delle **lifetimes**: il compilatore fa in modo che nessun riferimento sopravviva al proprietario da cui prende in prestito il valore.
```Rust
let x: &str;
{
	let y = "a";
	x = &y;
}
println!( "{}", x );
```
In questo esempio il compilatore si lamenta: _il lifetime di `y` e' diverso dal suo riferimento `x`_.

<u>Nota bene</u>: in realta', e' piu' complesso di cosi'... se per esempio eliminassimo la lettura di `x` con la `println`, il compilatore non darebbe errore.

In alcuni casi e' necessario fornire informazioni al compilatore sulle lifetimes, che non sempre sono facilmente inferibili:
```Rust
fn snd(a: &str, b: &str) -> &str {
	return if true { a } else { b }
}

fn main() {
	let a = "a";
	let b = "b";
	snd( &a, &b );
}
```
Il riferimento restituito da `snd`, deve avere il lifetime di `a` o di `b`? Sappiamo che e' di `a` perche' entra nel ramo in cui restituisce `a`... ma non e' sempre verificabile!

Per risolvere il problema usiamo i **parametri di lifetime**. Rust e' in grado di inferire autonomamente le lifetimes delle variabili, insieme ai tipi: quando scriviamo `let x = 5`, il sistema di tipi assegna il tipo `int` a `x`[^4] e _un nuovo parametro lifetime `'l`, che diventa vincolato da come usiamo il valore riferito_.

```Rust
struct S<'a,'b> {
	x: &'a i32,
	y: &'b i32,
	z: &’b i32
}

fn main() {
	let x = 10;
	let r;
	{
		let y = 20;
		{
			let s = S {
				x: &x,
				y: &y,
				z: &y
			};
			r = s.x;
		}
	}
	println!( "{}", r );
}
```

Nell'esempio, nella struct `S` dichiariamo due parametri di lifetime, dicendo che:
- `x` ha il lifetime di `'a`;
- `y` e `z` hanno il lifetime di `'b`;

In questo modo, il `main` e' compilabile! Infatti `s.x` ha il lifetime di `x`, per cui anche se lo scope di `s` finisce quando si stampa `r`, in realta' il suo lifetime e' quello di `x`, quindi rimane valido!

Se non specificassimo i lifetime, invece, il codice darebbe errore in fase di compilazione.

Per risolvere il caso precedente della funzione `snd`, scriveremo:
```Rust
fn snd<‘c,’d,’e>(a: &’c str, b: &’d str) -> &’e str {
	return if true { a } else { b }
}

fn main() {
	let a = "a";
	let b = "b";
	snd( &a, &b );
}
```

Oppure, _imponiamo che sia `a` che `b` condividano lo stesso lifetime_, e soprattutto che _il riferimento restituito da `snd` non superi in lifetime quello di `a` o `b`_:
```Rust
fn snd<‘l>(a: &’l str, b: &’l str) -> &’l str {
	return if true { a } else { b }
}
```

##### Riferimenti mutabili
I _valori presi in prestito da riferimenti mutabili sono raggiungibili esclusivamente tramite quel riferimento_ (neanche dall'owner!). Inoltre, per tutta la durata della lifetime del riferimento mutabile non deve esistere un altro percorso utilizzabile verso il suo valore o verso qualsiasi valore raggiungibile da esso.
![[ownership-and-references.png]]

## Referenze
- [[Tipi copia]]

[^1]: e' un po' lo stesso modo con cui quando una variabile esce dallo [[Scope|scope]] viene liberato il valore, ma generalizzato e controllabile!

[^2]: `Arc` e' per gestire casi di [[Concorrenza|concorrenza]]

[^3]: per evitare [[Race condition|race condition]]

[^4]: [[Tipaggio inferred|tipaggio inferito]]
