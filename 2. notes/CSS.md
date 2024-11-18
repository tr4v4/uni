---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 15:36:50
links:
  - "[[Lecture 07102024161340]]"
  - "[[Lecture 14102024161336]]"
  - "[[Lecture 16102024162932]]"
  - "[[Lecture 21102024161327]]"
  - "[[Lecture 24102024153025]]"
---
# CSS
---
## Introduzione
Per introdurre il CSS è bene conoscere un po' di:
- [[Tipografia|tipografia]]
- [[Font|font]]

## Definizione
> Il **CSS** (_Cascade Style Sheet_) è un linguaggio di stylesheet inizialmente introdotto per [[HTML]], ma utilizzabile su qualunque [[Markup|linguaggio di markup]].

E' _indipendente da HTML_, per cui la sua evoluzione non deve andare di pari passo con l'uscita di nuove versioni del linguaggio di markup.

## Utilizzo
Permette di essere usato su HTML assegnando gli stili ai suoi elementi in 3 modi:
- assegnandolo a tutti gli elementi di un certo tipo (`tag`);
- assegnandolo a tutti gli elementi di una certa categoria (`class`);
- assegnandolo a uno specifico elemento (`id`).

Può essere inserito:
- presso il tag di riferimento;
- nel tag `<style>`;
- nel tag `<link>` come file esterno.

### Sintassi
Uno _statement_ in CSS è l'_assegnazione di un attributo a una proprietà dell'elemento preso in considerazione_: `proprietà: valore`.

Le liste di statement sono inserite dentro i **selettori CSS**:
`selector {statement; statement; ...}

Per esempio
```css
h1 {
	color: white;
	background-color: black;
}
```

#### Selettori
Di selettori ce ne sono tantissimi:
- principali
	- **tipo**, es. `p`
	- **classe**, es. `.codice`
	- **id**, es. `#abc`
- pseudo-elementi
	- `first-line`
	- `first-letter`
	- `before` e `after` (con proprietà `content`)
- prossimità
	- ` `, indica la discendenza
	- `>`, indica solo i figli diretti
	- `~`, indica tutti i fratelli
	- `+`, indica il fratello immediato
- attributi
- pseudo-classi strutturali
	- `nth-child(n)`
	- `first-child`
- pseudo-classi
	- `active`
	- `hover`
	- `checked`

Degli esempi sono:
- `ul.list li:first-child {}`
- `ul.list li:nth-of-type(2) {}`
- `ul.list li:nth-of-type(odd) {}`
- `.nested > p:first-child`, dove `>` è per i figli diretti
- `.special-item ~ li {}` per i fratelli
- `.special-item + li {}` per i fratelli vicini (non tutti)

#### Tipi di dato
Le lunghezze sono importanti:
- _assolute_
	- `cm`, `mm`, `in`
	- `pt`
	- `pc`
	- `px` - assoluta ma dipendente dal device, perché ognuno ha una densità di pixel differente --> usarlo è pericoloso
- _relative_
	- `em` - larghezza della M maiuscola nel font selezionato, quindi è proporzionata al font selezionato; è relativa all'elemento padre
	- `ex` - altezza della x nel font selezionato
	- `ch` - larghezza dello 0
	- `lh` - altezza della riga
	- `vh`, `vw`
		- v sta per _viewport_, ossia la parte visibile della finestra, la sua dimensione al momento (può essere ridotta, ovviamente)
	- `rem` - come `em`, ma relativo all'elemento _root_ (il body)
	- `fr` - frazione del numero degli elementi previsti, ottimo per non fare i calcoli
	- `%` - trattamento diverso
		- a differenza di vh e vw, rappresenta la percentuale della dimensione rispetto al contenitore a cui appartiene, e non al viewport
		- nel font, fa sempre riferimento alla scatola contenitore

## Proprietà
### Scatola
Ogni spazio occupato da un elemento HTML è identificato da una **scatola**, che ne contiene il contenuto e ha un sacco di proprietà. Le scatole sono in relazione alle altre, e caratterizzate da _flusso_ e _posizione_.

#### Flusso
I flussi sono gestiti dalla proprietà `display`. Ogni elemento HTML ha un valore di display di default, ma può essere modificato a piacimento per modificare il modo in cui interagisce con gli altri elementi:
- `block`
- `inline`
- `table`, `table-row` e `table-cell`, per creare una tabella senza il tag `<table>`
- `list-item`
- `none`, per nascondere l'elemento
- `contents`
- `grid`, ha sostituito le tabelle di layout e i limiti della proprietà _float_
- `flex`, importantissimo, alla base delle pagine web più moderne, dinamiche e flessibili

#### Posizione
Se il flusso gestisce il modo in cui le scatole sono disposte e interagiscono tra di loro, la posizione è la proprietà effettiva del posizionamento delle scatole. Anche in questo caso, ci sono tanti attributi diversi a seconda del risultato richiesto:
- `static` (default), la scatola viene posta secondo il flusso normale che avrebbe normalmente
- `absolute`, stabilisco esattamente dove mettere la scatola
- `relative`, specifico un _delta_ rispetto alla posizione che avrebbe normalmente
- `fixed`, la scatola viene posta in posizione assoluta rispetto alla viewport, senza scrollare mai
- `sticky`, particolare

Come si specificano le posizioni in caso di posizionamenti che lo richiedono, quali `absolute` e `fixed`? Attraverso, per esempio, queste 4 proprietà: `left`, `right`, `top` e `bottom`.

#### Extra
Ci sono poi proprietà extra delle scatole:
- `z-index`, il canvas di default ha `z-index = -1`
- `overflow`, contenuto più grande della scatola, e c'è proprietà che consente di specificare come comportarsi in tal caso: `visible`, `hidden` e `scroll`
- `inherit`, un attibuto di qualunque proprietà, che consente di ereditare quella specificata nel padre

#### Elementi
Una scatola è composta nel seguente modo:
![[scatola-CSS.png]]

dove:
- _margin_ è la regione che separa una scatola dall'altra (sempre trasparente);
- _border_ è la regione del bordo della scatola;
- _padding_ è la regione di "respiro" tra il bordo e il contenuto (eredita il colore di sfondo di content);
- _content_ è la regione che contiene il contenuto;

#### Tipografia
- _font-size_
- _font-family_
- _font-weight_
- _font-style_
- _font-variant_
- _text-decoration_
- _text-indent_
- _text-align_
- _line-height_
- _text-align-last_
- _text-transform_
- _text-shadow_
- _font-stretch_
- _font-kerning_
- _letter-spacing_ e _word-spacing_
- _white-space_

### Canvas e viewport
In CSS:
- **canvas**
	- area virtuale di posizionamento degli elementi del [[DOM]] via CSS
	- è un piano cartesiano infinito, che parte in alto a sinistra da $(0, 0)$
- **viewport**
	- è la parte del canvas che è attualmente visibile attraverso lo schermo
	- quindi dipende dalla dimensione dello schermo
	- può muoversi sul canvas con lo scrolling

<u>Nota bene</u>: si può disegnare su _aree negative del canvas_, che non sono visualizzabili dalla viewport. Questo si chiama _off-screen drawing_, una tecnica che consente di disegnare fuori dallo schermo per tutto il tempo necessario al suo caricamento, e poi si trasformano le coordinate in positivo per far apparire il disegno nella pagina.

### Extra
#### Trasformazioni
Tra le proprietà sono importanti le trasformazioni, una serie di modifiche geometriche che si possono fare sugli elementi specificati da un selettore:
- `translate()`
- `translate3d()`
- `scale()`
- `scale3d()`
- `rotate()`
- `rotate3d()`
- `skew()`

<u>Nota bene</u>: bisogna scrivere anteponendo il prefisso `trasform:`.

#### `@` rules
Sono principalmente due:
- `@font-face`, per specificare e importare un font-family
- `@media`, per specificare regole dipendenti dal device

#### Animazioni
Si possono specificare animazioni di ogni genere, usando il selettore `@keyframes` e le proprietà `animation` e `transition`.

#### Variabili e calcoli aritmetici
Una variabile in CSS si chiama _custom property_, si definisce con `--` e si accede con `var(--nome)`. Si definiscono nella pseudo-classe `:root`, che ha scopo globale e non viene mai sovrascritto.

Per fare calcoli si usa `calc()`.


## Cascata
L'**algoritmo cascade** è una caratteristica peculiare di CSS. Ci possono essere _statement molteplici riguardanti le stesse proprietà di stessi elementi_: quale dev'essere effettivamente applicato? Dipende, da una serie di regole definite in questo [[Algoritmo|algoritmo]].

Intanto l'ordine delle specifiche CSS, ossia della scrittura dei selettori, gioca un ruolo importante: _solitamente vince sempre l'ultima specifica_.

Esiste l'attributo aggiuntivo `!important`, specificabile su qualunque proprietà, che impone all'algoritmo cascade di "far vincere" la regola specificata nella proprietà per quel selettore.

### Algoritmo
In poche parole, viene stabilito una scala gerarchica di valutazione delle regole specificate nel CSS. Bisogna infatti tenere conto dei seguenti fattori:
- _media-type_
- _importanza_ (attributo `!important`)
- _origine_
- _specificità_
- _ordine_ (di dichiarazione)

Solitamente, l'algoritmo valuta questi fattori nel seguente ordine:
1. dichiarazioni dello user-agent (il browser)
2. dichiarazioni dell'utente (il file CSS)
3. dichiarazioni normali dell'autore
4. dichiarazioni importanti dell'autore (`!important`)
5. dichiarazioni importanti dell'utente (`!important`)

## Referenze
