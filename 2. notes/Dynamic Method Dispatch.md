---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 21-10-2025 11:58:50
links:
  - "[[Lecture 14052025105842]]"
---
# Dynamic Method Dispatch
---
## Introduzione
> Il **Dynamic Method Dispatch** e' un meccanismo di [[Dynamic dispatch|dynamic dispatch]] implementato dalla [[JVM]] in [[Java]] in grado di risolvere il problema della [[Classe base fragile|classe base fragile]].

## Funzionamento
Java compila le [[Classe|classi]] separatamente le une dalle altre. In particolare, _ogni classe da' origine a un file_ che la macchina virtuale _carica dinamicamente_ quando il programma in esecuzione fa riferimento a quella classe[^1].

Questo file, di ogni classe, contiene la **constant pool**, contenente:
- variabili di istanza;
- metodi pubblici/privati;
- metodi e campi di altre classi;
- nomi di altre classi;
- ecc...;

La JVM fa riferimento ai _nomi_ (es. le variabili di istanza) trovati nel codice sorgente, come degli indici della constant pool, e non il nome stesso.
Per esempio
```Java
obj.variable = ...;
// viene interpretato come
obj.constantpool[5] = ...;
```

Quando **si incontra un nome per la prima volta, questo viene risolto**: vengono caricate dinamicamente le classi necessarie utilizzando le informazioni delle constant pool, controllati i [[Sistema di tipi|vincoli sui tipi]] e sulla visibilità (es. che il metodo invocato esista per la classe).

La **rappresentazione dei metodi nella constant pool è simile proprio alle [[VTable|vtable]]**: la pool della sottoclasse copia quella della superclasse, andando a sostituire i metodi sovrascritti con quelli ridefiniti ([[Sottotipaggio|overriding]]). A differenza delle vtable, però, **non calcoliamo staticamente gli offset**! Seguiamo invece queste 4 modalità di invocazione:
- `invokestatic` - il metodo è _statico_, non fa riferimento a `this`, e come sappiamo è risolto in [[Early binding|early binding]] (a compile-time);
- `invokevirtual` - il metodo è selezionato _dinamicamente_, in [[Late binding|late binding]], usando il classico dynamic dispatch implementato dalla vtable (seppur non si tratti effettivamente di vtable);
- `invokespecial` - usato o per l'invocazione statica di un [[Costruttore|costruttore]], che inizializza i campi `this`, oppure per l'invocazione dinamica di metodi `private` (invocati da metodi della classe stessa usando `this`); segue lo stesso percorso di `invokestatic`;
- `invokeinterface` - si chiama un metodo di [[Interfaccia|interfaccia]] che alcuni oggetti implementano; noi ignoriamo quale classe implementa il metodo dell'interfaccia, allora ispezioniamo l'oggetto per determinare se la sua classe implementa tale metodo e dove sono registrati i metodi dell'interfaccia all'interno della sua classe; **non assumendo uno schema fisso, che introdurrebbe il problema della classe base fragile**, cerchiamo nell'elenco delle interfacce implementate dalla classe, e una volta trovata procediamo in modo diretto --> calcoliamo una **itable** che rappresenta lo schema fisso comune a tutte le porzioni di classi che implementano l'interfaccia di destinazione, e usiamo l'offset dalla itable per trovare il metodo e procedere nello stesso modo delle invocazioni virtuali (`invokevirtual`);
- `invokedynamic`;

L'idea fondamentale e' che a differenza delle vtable, la JVM non calcola degli offset statici, ma dei riferimenti simbolici nella constant pool per ogni metodo.

### In pratica
La JVM risolve questa fragilità non basandosi interamente su offset precalcolati, ma introducendo una fase di **risoluzione dinamica** (runtime) dei riferimenti:
1. **Compilazione e Constant Pool:** In Java, la compilazione delle classi avviene separatamente, e ogni classe genera un file contenente la sua **tabella dei simboli** (`constant pool`). Questa tabella contiene tutte le informazioni necessarie, inclusi i nomi dei metodi utilizzati nella classe.
2. **Lookup Dinamico:** Quando un metodo viene invocato, la JVM accede al `constant pool` della classe per recuperare il nome del metodo. Inizialmente, la macchina astratta esegue una ricerca (lookup) per **nome**.
3. **Calcolo e Salvataggio dell'Offset:** La JVM ricerca il nome del metodo nella _vtable_ (o struttura equivalente) della classe e determina il suo **offset**. L'offset, sebbene utile per l'accesso, non è determinato staticamente. Dopo essere stato calcolato a runtime, l'offset viene **salvato** (ad esempio, tramite la riscrittura dell'istruzione bytecode, tecnica chiamata _quickened instruction_) per un utilizzo futuro.
4. **Mitigazione della Fragilità:** Le successive invocazioni dello stesso metodo sullo stesso oggetto (o su oggetti della stessa classe) utilizzano direttamente l'offset salvato, evitando di ripetere la costosa ricerca per nome. Poiché la risoluzione iniziale e il calcolo dell'offset avvengono in modo dinamico la prima volta che il nome viene referenziato, la JVM non si affida a offset statici potenzialmente obsoleti, ma si adatta dinamicamente a eventuali modifiche gerarchiche intervenute tra le classi caricate.

## Referenze

[^1]: una sorta di [[Linking dinamico|linking dinamico]] ma per le classi
