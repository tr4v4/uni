---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 09-10-2023 19:14:31
links:
  - "[[Lecture 09102023132029]]"
  - "[[Lecture 05102023130513]]"
---
# Codifica floating-point
---
## Introduzione
Per rappresentare tante informazioni in maniera compatta, e quindi sia numeri grandissimi che piccolissimi, usiamo la _notazione esponenziale_. Esempi:
- $9 \times 10^{-8}$
- $2 \times 10^{33}$

Questa formattazione risulta molto efficace per i calcolatori, perché consente di memorizzare con facilità informazioni altrimenti irrappresentabili. In particolare, la tecnica che sfrutta questa notazione si chiama **virgola mobile** (o _floating-point_).

## Tecnica
Con il floating-point si va a definire _ogni_ numero nella forma
$$n = f \times 10^{e}$$
dove:
- $f$ è detto frazione o **mantissa**
- $e$ è detto esponente o **caratteristica**

### Normalizzazione
I numeri in virgola mobile possono essere rappresentati in infiniti modi, ma come standard si dice che devono essere _normalizzati_, ovvero rispettare le seguenti leggi:
- la mantissa dev'essere della forma $0,...$
- le cifre dopo la virgola della mantissa non devono cominciare con $0$

#### Esempio
Se volessimo rappresentare 53 in virgola mobile e normalizzato allora dovremmo:
1. _convertirlo in binario_: `53 --> 110101,0`
2. _normalizzarlo_: `0,110101 x 2^6`

A questo punto, a seconda del **formato** scelto (è una convenzione), si struttura la sequenza di bit che rappresenta il numero in floating-point. In questo caso usiamo il formato:
- 1 bit _segno_
- 23 bit _mantissa_
- 8 bit _esponente_ in [[Complemento a 2|complemento a 2]]

Il risultato sarà allora
> **(0) (110101 00000000000000000) (00000 110)**
> dove
> - il primo gruppo (bit) rappresenta il segno
> - il secondo gruppo la mantissa (_notare che essendo dopo la virgola gli zeri meno significativi finiscono a destra_)
> - il terzo gruppo l'esponente (in questo caso positivo)

Lo stesso discorso si fa per qualsiasi altro numero. Fare quindi attenzione alla [[Conversione binario-decimale#Numero con la virgola|conversione per i numeri con la virgola]].

### Formati standard
- [[BINARY32]]
- [[BINARY64]] (i `double` del [[C]]/[[C++]])

## Problemi
Seppur efficiente, questa tecnica ha dei limiti significativi. In particolare:
- **underflow** --> i numeri troppo piccoli vengono confusi con lo 0
- **overflow** --> i numeri troppo grandi (sia positivi che negativi) non si riescono a rappresentare
- **precisione finita** --> _non si riescono a rappresentare tutti i numeri_

### Esempio
E' per questa ragione che il seguente codice produce per 0 un output che sembra sbagliato:
```cpp
for (double i = -1.0; i <= 1.0; i += 0.2) {
	cout << i << endl;
}
```
Output:
```
-1.0
-0.8
-0.6
-0.4
-0.2
3.35e-20
0.2
0.4
0.6
0.8
1.0
```

Infatti `0.2` in _virgola-mobile_ (e quindi in binario) è un numero periodico, perciò ad ogni calcolo si semplificano dei risultati che portano lo 0 a non essere effettivamente 0.

## Referenze