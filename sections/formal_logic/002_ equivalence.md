# Logical Equivalence

Now that we've covered that we can make very large tables that show all the possible outcomes of a logical statement, we can get into a new concept: Equivalence.  This is a fancy mathy way of saying that if you have two statements with the same outputs, they are interchangable.

A more formal definition would be:
> Two statements $p$ and $q$ are said to be logically equivalent, or $p \equiv q$, if and only if $p \leftrightarrow q$ is a [tautology](https://en.wikipedia.org/wiki/Tautology_\(logic\)).

## Tautology

However, that definition has a brandy new \$5 philosophy word: Tautology.  For our purposes, a tautology is a statement where no matter what you put in for the variables, it will always output `true`.

For example, the statement $P \wedge \neg P$, which you can read as `C or not C` or as "Cats are awesome, or cats are not awesome", will always evaluate to `true`:
| $C$ | $\neg C$ | $C \wedge \neg C$ |
| :-: | :------: | ----------------- |
|  T  |    F     | T                 |
|  F  |    T     | T                 |

## And back to equivalence

So, now that we know what a tautology, we need to figure out how to make `if and only if ... then` ($\leftrightarrow$) always output `true`.  We can see from this truth table that $p \leftrightarrow q$ is only true if $p$ and $q$ are matching:

| $p$ | $q$ | $p \leftrightarrow q$ |
| :-: | :-: | :-------------------: |
|  T  |  T  |           T           |
|  T  |  F  |           F           |
|  F  |  T  |           F           |
|  F  |  F  |           T           |

So let's say that $p$ is the statement $\neg(A \wedge B)$:
| $A$ | $B$ | $A \wedge B$ | $\neg(A \wedge B)$ |
| :-: | :-: | :----------: | :----------------: |
|  T  |  T  |      T       |         F          |
|  T  |  F  |      F       |         T          |
|  F  |  T  |      F       |         T          |
|  F  |  F  |      F       |         T          |

And $q$ is the statement $\neg A \cap \neg B$:
| $A$ | $B$ | $\neg A \cap \neg B$ |
| :-: | :-: | :------------------: |
|  T  |  T  |          F           |
|  T  |  F  |          T           |
|  F  |  T  |          T           |
|  F  |  F  |          T           |

We can line up the truth tables, and add in our final statement now:
| $\neg(A \wedge B)$ | $\neg A \cap \neg B$ | $\neg(A \wedge B) \leftrightarrow \neg A \cap \neg B$ |
| :----------------: | :------------------: | :---------------------------------------------------: |
|         F          |          F           |                           T                           |
|         T          |          T           |                           T                           |
|         T          |          T           |                           T                           |
|         T          |          T           |                           T                           |

So now you can see that these two statements are logically equivalent, and that leads us into our next session nicely:

## Useful Logical Equivalences

We're going to cover some useful equivalences, as well as some code demonstrating this.  This isn't production code so much as examples to show you what this logic could look like when you translate it to JS and Python.

### Commutative Law

This is just a fancy way of saying that the logical operators `and` and `or` don't care about the order of the variables to either side of them.

#### Logic
$P \wedge Q \equiv Q \wedge P$

#### Python
```python
p = True
q = True

if p and q:
    print("P ∧ Q is True")

if q and p:
    print("Q ∧ P is True")

if p or q:
    print("P ∩ Q is True")

if q or p:
    print("Q ∩ P is True")
```

#### JavaScript
```js
let p = true;
let q = true;

if (p && q) {
    console.log("P ∧ Q is True");
}
if (q && p) {
    console.log("Q ∧ P is True");
}
if (p || q) {
    console.log("P ∩ Q is True");
}
if (q || p) {
    console.log("Q ∩ P is True");
}
```

### Associativity Law

This is just saying that if you are chaining `and` or `or` together, you can put the parenthesis however you want, and the output will not change.

#### Logic
$P \wedge (Q \wedge R) \equiv (P \wedge Q) \wedge R$

#### Python
```python
p = True
q = True
r = True

if p and (q and r):
    print("P ∧ (Q ∧ R) is True")

if (q and p) and r:
    print("(P ∧ Q) ∧ R is True")
```

#### JavaScript
```js
let p = true;
let q = true;
let r = true;

if (p && (q && r)) {
    console.log("P ∧ (Q ∧ R) is True");
}
if ((q && p) && r) {
    console.log("(P ∧ Q) ∧ R is True");
}
```

### De Morgan's Law

First off, De Morgan wrote a lot of laws.  If you study math, you will find more De Morgan's Laws.  They never say what field they are for, they are all just De Morgan's Law.

Demogorgon's law states that `and` and `or` are logical opposites from each other, so when negating a statement that contains them you have to also flip any `and` to an `or` at the same time.

#### Logic
$\neg(P \wedge Q) \equiv \neg P \cap \neg Q$

#### Python
```python
for p in (True, False):
  for q in (True, False):
    for r in (True, False):
      statement_one = all([not p, not q, not r])
      statement_two = not any([p, q, r])
      print(f"p: {p}, q: {q}, r: {r}")
      print(f"¬p ∧ ¬q ∧ ¬r: {statement_one}")
      print(f"¬(p ∩ q ∩ r):  {statement_two}")
      print("----")

```

#### JavaScript
```js
for (let p of [true, false]) {
  for (let q of [true, false]) {
    for (let r of [true, false]) {
      let s1 = [!p, !q, !r].every();
      let s2 = !([p, q, r].some());
      console.log(`p: ${p}, q: ${q}, r: ${r}`)
      console.log(`¬p ∧ ¬q ∧ ¬r: ${s1}`)
      console.log(`¬(p ∩ q ∩ r):  ${s2}`)
      console.log("----")
    }
  }
}
```



----
[Index](/README.md#sections) | [Next](/sections/sets/index.md)

