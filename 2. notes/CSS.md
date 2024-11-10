---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 15:36:50
links:
  - "[[Lecture 07102024161340]]"
  - "[[Lecture 14102024161336]]"
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
Di selettori ce ne sono tantissimi, ma i principali sono:
- tipo, es. `p`
- classe, es. `.codice`
- id, es. `#abc`

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
- _flusso blocco_
- _flusso inline_
- _flusso float_
- ...

Ce ne sono altri importanti come _flex_ e _grid_.

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

## Cascata
L'**algoritmo cascade** è una caratteristica peculiare di CSS. Ci possono essere _statement molteplici riguardanti le stesse proprietà di stessi elementi_: quale dev'essere effettivamente applicato? Dipende, da una serie di regole definite in questo [[Algoritmo|algoritmo]].

Intanto l'ordine delle specifiche CSS, ossia della scrittura dei selettori, gioca un ruolo importante: _solitamente vince sempre l'ultima specifica_.

## Referenze