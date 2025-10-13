---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 19:13:59
links:
  - "[[Lecture 19032025113725]]"
  - "[[Lecture 24042025131115]]"
---
# Eccezione
---
## Introduzione
> Un'**eccezione** è un _evento che si verifica durante l'esecuzione di un [[Programma|programma]] e che interrompe il normale flusso di istruzioni_. Si tratta a tutti gli effetti di un costrutto di programmazione, che consente di gestire in modo elegante gli errori e le situazioni impreviste, nonche' di migliorare l'efficienza di esecuzione del programma stesso.

## Idee
Potremmo rappresentare gli errori attraverso i [[Tipi monadici|tipi monadici]], in particolare i tipi `Result`. Con questi, infatti, viene incapsulata all'interno del tipo sia il valore del risultato che l'eventuale errore. Tuttavia questo sistema diventa complesso quando si annidano le operazioni...

### Codici di ritorno
Un'idea naive usata molto agli esordi della programmazione, e di fatto ancora oggi nelle [[System call|system calls]], consiste nel definire dei _valori eccezionali_ restituiti dalla funzione in causa associati a un certo significato.

Di solito sono interi, come `0`, `1` (o più per aumentarne la granularità), che rispettivamente vogliono dire:
- `0` - tutto bene;
- `1` - _errore_.

Il problema di questo approccio è che **i valori eccezionali fanno parte o possono far parte del dominio di ritorno della funzione**, quindi si crea facilmente dell'ambiguità che non è risolvibile in modo elegante.

### Inversione del controllo
Un altro sistema, detto di _inversione del controllo_, consiste nel **passare alla funzione [[Invocazione di procedura|invocata]] un'altra funzione da eseguire in caso di errore**: è terribile, in quanto richiede sapere come viene usata quella funzione all'interno del chiamato, e quindi una sincronizzazione tra chiamante e chiamato inutile...

### Eccezioni
E' per questo che nascono le **eccezioni**, che prende spunto dall'inversione del controllo. L'idea è, in caso di errore all'interno di una funzione, di _trasferire il controllo a un gestore di eccezioni_, definito in qualche punto dello stack di chiamate del programma. Il gestore può trovarsi:
- nella funzione che genera l'eccezione;
- nella funzione che ha invocato la funzione che genera l'eccezione;
- da nessuna parte --> in questo caso il programma non può che bloccarsi[^1].

Sotto le quinte, in realtà, quello che succede è che un'eccezione è un tipo returnato da una funzione in caso di errore, che viene catturato da un meccanismo di [[Pattern matching|pattern matching]]. Di conseguenza, _il tipo returnato dalla funzione è in realtà un [[Tipo somma|tipo somma]]_: il tipo di ritorno + ogni altra eccezione "lanciabile"!

## Reale implementazione
### Try-catch
![[eccezione-esempio.png]]

E' importante notare che **il blocco `try` non è eseguito [[Azione atomica|atomicamente]]**! Ma viene eseguito passo passo fino a che un'istruzione non solleva un'eccezione: _lì subentra il codice del gestore di riferimento_, definito nel `catch`.

#### Eccezioni
Il blocco `catch` fa riferimento a un'eccezione, [[Overriding|sottotipo]] di `Throwable`, legata a un nome. In [[Java]] la gerarchia di sottotipaggio dei `Throwable` è la seguente:
![[throwable-java.png]]

Di fatto quindi i `Throwable` si dividono principalmente in:
- `Error`;
- `Exception`.

Il [[Sistema di tipi|sistema di tipi]] di Java obbliga lo sviluppatore a gestire esplicitamente qualunque sottotipo di `Throwable` tranne:
- `Error`;
- `RuntimeException` (sottotipo di `Exception`).

Questo perché questi due _rappresentano fallimenti irrecuperabili a livello di runtime e di applicazione_: **devono interrompere l'esecuzione del programma**, se non nei casi specifici (catturabili con `try` e `catch`) in cui il programmatore sa come gestirli.

### Funzionamento
#### Gestore
Il gestore dell'eccezione e' legato in modo statico al blocco di codice protetto, cosi' _quando viene eseguito rimpiazza la parte di blocco che doveva essere ancora eseguita_.

#### Propagazione
Se l'eccezione non e' gestita nella routine corrente, viene propagata al chiamante; se a sua volta non e' gestita dal chiamante, viene propagata al chiamante del chiamante, risalendo di fatto la [[Catena dinamica|catena dinamica]]. Alla fine, se non viene gestita da nessuno, si raggiunge il top-level, ovvero il sistema operativo, che si occupa di gestirla in modo generico.

Ad ogni livello della catena dinamica che propaga l'eccezione, viene tolto il suo [[Record di attivazione|record di attivazione]] e ripristinati i registri.

#### Implementazione
##### Naive
Possiamo pensare di usare una [[Pila|pila]] in cui andare a inserire i gestori ogni volta che si entra in un `try`: quando c'e' un'eccezione si toglie dalla pila il gestore, e se non e' quello giusto risollevi l'eccezione e si continua a togliere dalla pila finche' non troviamo il gestore giusto.

Non e' il massimo perche' abbiamo un overhead di tempo e spazio.

##### Migliore
- il compilatore genera una tabella dove, per ogni blocco protetto e per ogni routine, c’è una coppia `<block_addr, handler_addr>`
- la tabella è ordinata sul primo elemento (staticamente)
- al sollevamento di un’eccezione:
	- ricerca binaria nella tabella del ProgCounter sul primo elemento
	- trasferimento del controllo all’indirizzo corrispondente del gestore
- se il gestore risolleva l’eccezione, ripeti
- attenzione: se il gestore è quello nascosto di una routine la prossima ricerca nella tabella deve avvenire non col PC, ma con l’indirizzo di ritorno della routine

## Referenze

[^1]: in realtà va al gestore di eccezioni del run-time, che blocca il programma
