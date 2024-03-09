---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 30-11-2023 15:39:17
links:
  - "[[Lecture 23112023091708]]"
---
# Induzione strutturale
---
## Introduzione
> Per **induzione strutturale** si intende una _tecnica utilizzata per dimostrare determinate proprietà su [[Funzione informatica|funzioni]] definite per [[Ricorsione strutturale|ricorsione strutturale]]_.

## Composizione
E' analoga alla ricorsione strutturale, perché prevede:
1. una sotto-dimostrazione per ogni forma del [[ADT|tipo di dato algebrico]] del problema;
2. per ogni sotto-dimostrazione viene assunto che la proprietà $P$ valga su tutti i parametri formali contenuti nel pattern ($\omega$[^1]) --> **ipotesi induttiva**.

Di fatto l'induzione strutturale è definibile come **una funzione strutturalmente ricorsiva che genera una dimostrazione**.

### Fasi
Una dimostrazione per induzione strutturale si suddivise nelle seguenti fasi:
1. **fase di proclamazione**: per dimostrare $\forall x. P$ si procede per casi su $x$ per dimostrare $P$, che deve contenere una chiamata $f$ dove $f$ è definita per ricorsione strutturale
2. per ogni pattern di $x$
	- **caso $\omega$**
		1. **ipotesi induttive**: si attua una [[Sostituzione|sostituzione]] per ogni parametro formale di $\omega$ dello stesso tipo di $x$ e si tiene come ipotesi
		2. **fase di enunciazione**: ricalco ciò che sto dimostrando, sostituendo al posto di $x$ il pattern in causa $\omega$ ($P[\omega/x]$)
		3. **fase di semplificazione**: tradurre $P[\omega/x]$ per ciò che $\omega$ vale in $f$
		4. **fase di prova**: proseguire come una normale dimostrazione in [[Logica del primo ordine|logica del prim'ordine]], usando anche le ipotesi induttive

### Esempio
Tenendo come riferimento la definizione del tipo di dato algebrico dei _numeri naturali_
$$\mathbb{N} ::= O \ | \ S \ \mathbb{N}$$

dove $S$ significa "il successore di", e la funzione per la _somma di numeri naturali_ definita per ricorsione strutturale
$$O + m = m$$
$$(S \ n) + m = S \ (n + m)$$

vogliamo dimostrare:
$$\forall n \in \mathbb{N}, \ n + 0 = n$$

#### Dimostrazione
Procedo per casi su $n$ per dimostrare $\forall n \in \mathbb{N}, \ n + 0 = n$.
_Caso 0_:
- devo dimostrare $0 + 0 = 0$
	- equivalente a $0 = 0$
- ovvio per la [[Riflessività di una relazione|proprietà riflessiva]] dell'uguaglianza

_Caso $S \ n$_:
- ipotesi induttiva: $n + 0 = n$ (II)
- devo dimostrare $S \ n + 0 = S \ n$
	- equivalente a $S (n + 0) = S \ n$
- ovvio per II e la proprietà riflessiva dell'uguaglianza

**Qed**.

<u>Nota bene</u>: ci sono dimostrazioni di certi teoremi che obbligano il dimostratore a dover dimostrare dei _lemmi_ al fine di completare la dimostrazione.

## Referenze
[^1]: si veda la [[Linguaggio di programmazione funzionale#Definizione di funzioni|definizione di funzione dei linguaggi funzionali]]