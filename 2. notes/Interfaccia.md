---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 15-03-2024 15:57:08
links:
  - "[[Lecture 12032024111356]]"
  - "[[Lecture 13032024111045]]"
---
# Interfaccia
---
## Introduzione
> Un'**interfaccia** in [[Java]], funge un po' da [[Prototipo vs Implementazione|prototipo]] da seguire alle classi, [[Classe astratta|astratte]] e concrete, che la implementano. Forniscono appunto solo l'interfaccia, ovvero una serie di [[Funzione informatica#Firma|firme di metodi]] che le classi che la implementano (con la keyword `implements`) dovranno implementare.

## Utili
### `Comparable`
Un'interfaccia fondamentale _built-in_ di Java che usiamo per implementare [[Algoritmo di ordinamento|algoritmi di ordinamento]] su oggetto [[Generics|generici]] è `Comparable`. Espone unicamente il metodo `public int compareTo(Object o)`, e vale:
- `-1`, se l'oggetto su cui il metodo viene chiamato _precede_ l'oggetto `o` passato come parametro
- `0`, se sono equivalenti rispetto all'ordinamento
- `1`, se l'oggetto su cui il metodo viene chiamato _viene dopo_ l'oggetto `o` passato come parametro

### `Iterator`
Questa interfaccia ci permette di _allocare un iteratore_, ovvero un _cursore che scorre oggetti di una classe che implementano tale interfaccia_. Espone come unico metodo `Iterator<T> iterator();`, che restituisce un oggetto `Iterator`[^1] che a sua volta espone due metodi: `boolean hasNext();` per verificare se c'è un altro elemento e `T next();` per ritornare l'elemento successivo.

Gli oggetti che implementano tale interfaccia, detti _iterabili_, possono essere scansionati da una struttura di controllo chiamata `for-each`[^2].

#### Esempi
Possiamo scansionare gli elementi di un `ArrayList` e di un `LinkedList`.

##### `ArrayList`
```java
ArrayList<Integer> L = new ArrayList<>();
L.add(1); L.add(2); L.add(3);

int sum1 = 0;
Iterator iter = L.iterator();
while(iter.hasNext())
	sum1 = sum1 + iter.next();

int sum2 = 0;
for(Integer n: L)
	sum2 = sum2 + n;

int sum3 = 0;
for(int i = 0; i < L.size(); i++)
	sum3 = sum3 + L.get(i);

System.out.println(sum1 + " " + sum2 + " " + sum3);
```

##### `LinkedList`
```java
LinkedList<Integer> L = new ArrayList<>();
L.add(1); L.add(2); L.add(3);

int sum1 = 0;
Iterator iter = L.iterator();
while(iter.hasNext())
	sum1 = sum1 + iter.next();

int sum2 = 0;
for(Integer n: L)
	sum2 = sum2 + n;

int sum3 = 0;
for(int i = 0; i < L.size(); i++)
	sum3 = sum3 + L.get(i);

System.out.println(sum1 + " " + sum2 + " " + sum3);
```

## Referenze
[^1]: di tipo [[Generics|generic]]
[^2]: un [[Comandi iterativi#For|ciclo for]] per oggetti