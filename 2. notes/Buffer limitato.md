---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 20-11-2024 23:24:17
links:
  - "[[Lecture 07112024092537]]"
---
# Buffer limitato
---
## Introduzione
> Il **buffer limitato** è una variante del [[Produttore e consumatore|problema del produttore e consumatore]], uno dei [[Problemi classici della programmazione concorrente|problemi classici della programmazione concorrente]], in cui la variabile condivisa è un buffer di _capacità massima_ (un [[Array|array]] di elementi). Anche in questo caso bisogna garantire le seguenti proprietà:
> - il _producer non deve sovrascrivere elementi del buffer prima che il consumer abbia effettivamente utilizzato i relativi valori_;
> - il _consumer non deve leggere due volte lo stesso valore, ma attendere che il producer abbia generato il successivo_;
> - assenza di [[Deadlock|deadlock]];
> - assenza di [[Starvation|starvation]].

## Implementazione
Ancora possiamo usare i [[Semafori|semafori]] per risolvere il problema:
```C
Queue q(maxsize = SIZE);
Semaphore empty = new Semaphore(SIZE);
Semaphore full = new Semaphore(0);
Semaphore mutex = new Semaphore(1);

process Producer {
  while (true) {
    Object val = produce();
    empty.P();
    mutex.P();
    q.enqueue(val);
    mutex.V();
    full.V();
  }
}

process Consumer {
  while (true) {
    full.P();
    mutex.P();
    Object val = q.dequeue();
    mutex.V();
    empty.V();
    consume(val);
  }
}
```

<u>Nota bene</u>: in questo caso, è necessario un semaforo `mutex` perché il buffer è una variabile condivisa con una grandezza limitata, e _`empty.P()` (per i produttori) e `full.P()` (per i consumatori) non sono per forza bloccanti_. Per esempio, se `empty` ha valore 3, due produttori possono tranquillamente fare `empty.P()` e accedere al buffer simultaneamente, ma ciò non va bene perché il buffer `q` è condiviso. Quindi serve un semaforo `mutex` per garantire la mutua esclusione. Lo stesso ragionamento vale per i consumatori nel caso di `full.P()`.

## Referenze