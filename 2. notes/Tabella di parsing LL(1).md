---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 27-08-2025 18:49:42
links:
  - "[[Lecture 07112024120244]]"
---
# Tabella di parsing LL(1)
---
## Introduzione
> La **tabella di parsing $LL(1)$** e' una [[Matrice|matrice]] usata dai [[Parser top-down|parser top-down]] per risolvere il nondeterminismo nei linguaggi $LL(1)$, usando i meccanismi di [[Look-ahead|look-ahead]] di [[First e follow|first e follow]].
> Formalmente si tratta di una matrice bidimensionale $M$ in cui:
> - _le righe contengono i nonterminali $NT$_;
> - _le colonne contengono i terminali $T$ e il \$ di fine stringa_;
> - _ogni casella $(A, a)$ contiene le produzioni che possono essere scelte dal parser mentre tenta di espandere $A$ (sulla pila) e l'input corrente e' $a$_.

Quindi, **se ogni casella contiene al piu' una produzione, allora il parser e' deterministico** e di tipo $LL(1)$.

## Riempimento
La tabella si riempie nel seguente modo:
- per ogni produzione $A \to \alpha$:
	1. per ogni $a \in T$ tale che $a \in \text{First}(\alpha)$, inserisci $A \to \alpha$ in $M[A, a]$;
	2. se $\epsilon \in \text{First}(\alpha)$, inserisci $A \to \alpha$ in tutte le caselle $M[A, x]$ per $x \in \text{Follow}(A)$ (nota che $x$ puo' essere \$);

Ogni casella vuota rappresenta uno stato di errore --> la funzione ricorsiva chiama `Fail()`.

Infatti rispettivamente le 2 regole ci dicono:
1. **ogni volta che sulla pila c'e' $A$ e il carattere in input e' un first di $\alpha$ della produzione $A \to \alpha$, scelgo quella produzione**;
2. **ogni volta che sulla pila c'e' $A$ e il carattere in input e' un suo follow, scelgo la produzione $A \to \alpha$ sapendo che tra i first di $\alpha$ c'e' $\epsilon$, con l'intento di annullarlo!**.

### Esempio
Consideriamo la [[Fattorizzazione a sinistra|grammatica fattorizzata a sinistra]]
$$E \to TE' \ \ \ \ \ E' \to \epsilon | +E | -E \ \ \ \ \ T \to AT' \ \ \ \ \ T' \to \epsilon|*T \ \ \ \ \ A \to a|b|(E)$$
e calcoliamo first e follow:

|      | $\text{First}$   | $\text{Follow}$  |
| ---- | ---------------- | ---------------- |
| $E$  | $a, b, ($        | $), \$$          |
| $E'$ | $+, -, \epsilon$ | $), \$$          |
| $T$  | $a, b, ($        | $+, -, ), \$$    |
| $T'$ | $*, \epsilon$    | $+, -, ), \$$    |
| $A$  | $a, b, ($        | $*, +, -, ), \$$ |

A questo punto, ci creiamo la tabella di parsing $LL(1)$:

|      | $+$               | $-$               | $*$         | $($          | $)$               | $a$          | $b$          | $\$$              |
| ---- | ----------------- | ----------------- | ----------- | ------------ | ----------------- | ------------ | ------------ | ----------------- |
| $E$  |                   |                   |             | $E  \to TE'$ |                   | $E  \to TE'$ | $E  \to TE'$ |                   |
| $E'$ | $E' \to +E$       | $E' \to -E$       |             |              | $E' \to \epsilon$ |              |              | $E' \to \epsilon$ |
| $T$  |                   |                   |             | $T \to AT'$  |                   | $T \to AT'$  | $T \to AT'$  |                   |
| $T'$ | $T' \to \epsilon$ | $T' \to \epsilon$ | $T' \to *T$ |              | $T' \to \epsilon$ |              |              | $T' \to \epsilon$ |
| $A$  |                   |                   |             | $A \to (E)$  |                   | $A \to a$    | $A \to b$    |                   |

Ogni casella contiene al piu' una produzione, per cui la grammatica e' $LL(1)$.

## Referenze
- [[Grammatiche LL(1)]]