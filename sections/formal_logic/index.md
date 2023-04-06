# Formal Logic
Formal or mathematical logic is a set of tools for forming arguments out of statements (e.g. `VS Code is the best GUI text editor`) and connectives (e.g.: `and` or `or`).

Formal logic is at the core of programming: you write statements to control program flow.  For example, you might write `someVar == "some value"` to evaluate if `someVar` is equal to the value `"some value"`.  We can use what we are learning here to represent those, and gain some insight into how those statements work.

## Truthiness
Unlike reality, everything within the field of formal logic is either `true` or `false`.  One way to think of truthiness is like a lightswitch: `true` means that the switch on, and `false` means that the switch is off.

## Statements
Statements are sentences that are either `true` or `false`.  For example: `Cats are awesome`.  Other statements could be `Dogs are awesome`, or `Vim is the best command line text editor`.  Finally, we can represent these statements as variables:
- Cats are awesome = $C$
- Dogs are awesome = $D$

## Connectives
Connectives are how we join together statements to express more complicated ideas.  For example, we might have the following statements that we want to join in novel ways:
- `Cats are awesome`
- `Dogs are awesome`

We can join these with any number of connectives, making novel new combinations like:
- `Cats are awesome or dogs are awesome`
- `Cats are awesome and dogs are awesome`
- `If cats are awesome then dogs are awesome`

The connectives (and their symbols) that we will be covering in this unit are:
- `and`: $\wedge$
- `or`: $\cap$
- `not`: $\neg$
- `if ... then`: $\rightarrow$
- `if and only if ... then`: $\leftrightarrow$

Using these symbols, and our variables from earlier, we can rewrite our statements in shorter ways:
- $C \wedge D$
- $C \cap D$
- $C \rightarrow D$

## Evaluating statements
Now that we have established some ground rules, let's talk about evaluating these statements.  Since we are making logical arguments (barring the one I started about emacs and Vim earlier), we aren't going to declare a variable as `true` or `false` just yet, but we're going to assume that they could be either and look at all the possible outcomes of the statement.

We can show all the possible outcomes of a statement with a truth table.  For example, the truth table for the statement `Cats are awesome` would be:

| $C$ |
|:---:|
| T   |
| F   |

Adding in some complexity, the truth table for `Cats are awesome and dogs are awesome` would be:

| $C$ | $D$ | $C \wedge D$ |
| :-: | :-: | :----------: |
|  T  |  T  |      T       |
|  T  |  F  |      F       |
|  F  |  T  |      F       |
|  F  |  F  |      F       |

It's worth noting that the second table is longer than first table.  Since the first table has 2 rows, and the second has 4 rows, the next table is definitely going to be larger, but how much larger?  Let's make some guesses:

- Guess 1:
  - Truth tables grow at 2 rows per variable.
- Guess 2:
  - Truth tables double in length for each variable.

----

We can validate our guess by making a truth table to cover all the possibilities of the statement `Cats are awesome and dogs are awesome and bats are awesome` (seriously, bats are awesome and [adorable](https://upload.wikimedia.org/wikipedia/commons/b/b4/Bat_Week_2017_-_Congressional_Reception_%2837237943654%29_%28cropped%29.jpg)), which has 3 variables:

| $C$ | $D$ | $(C \wedge D)$ | $B$ | $(C \wedge D) \wedge B$ |
| :-: | :-: | :------------: | :-: | :---------------------: |
|  T  |  T  |       T        |  T  |            T            |
|  T  |  T  |       T        |  F  |            F            |
|  T  |  F  |       F        |  T  |            F            |
|  T  |  F  |       F        |  F  |            F            |
|  F  |  T  |       F        |  T  |            F            |
|  F  |  T  |       F        |  F  |            F            |
|  F  |  F  |       F        |  T  |            F            |
|  F  |  F  |       F        |  F  |            F            |

Since this table has 8 rows, it looks like the length of a truth table doubles for every new variable we add.

## Truth Tables

So, we've got the basic concepts, not let's look at truth tables for each connective!  We're going to use the following variables for each statement:
- Cats are awesome = $C$
- Dogs are awesome = $D$

### AND
`And` is only `true` when both the left and right sides are `true`.

Example:
- `Cats are awesome and dogs are awesome`
- $C \wedge D$

| $C$ | $D$ | $C \wedge D$ |
| :-: | :-: | :----------: |
|  T  |  T  |      T       |
|  T  |  F  |      F       |
|  F  |  T  |      F       |
|  F  |  F  |      F       |

### OR
`Or` is `true` when either the left or the right side is `true`.

Example:
- `Cats are awesome or dogs are awesome`
- $C \cap D$

| $C$ | $D$ | $C \cap D$ |
| :-: | :-: | :--------: |
|  T  |  T  |     T      |
|  T  |  F  |     T      |
|  F  |  T  |     T      |
|  F  |  F  |     F      |

### NOT
`Not` inverts a value.

Example:
- `Cats are not awesome` ☹️
- $\neg C$

| $C$ | $\neg C$ |
| :-: | :------: |
|  T  |    F     |
|  F  |    T     |

### If $\rightarrow$ Then
`If ... then` is only false if the left side of the operator is `true` and the right side is `false`.  You can rephrase this as "if $X$ is true, then $Y$ must be true".  This one is a little tricky, because `if ... then` is always `true` if the lefthand side is `false`.

Example:
- `If cats are awesome then dogs are awesome`
- $C \rightarrow D$

| $C$ | $D$ | $C \rightarrow D$ |
| :-: | :-: | :---------------: |
|  T  |  T  |         T         |
|  T  |  F  |         F         |
|  F  |  T  |         T         |
|  F  |  F  |         T         |

### If $\leftrightarrow$ Then (If and only if)
This is the stricter version of `if ... then`: this is only `true` if both sides match.  You can also write this statement in shorthand as `Iff ... then`, but at the cost of everyone telling you that you made a typo.

Example:
- `If and only if cats are awesome, then dogs are awesome`
- $C \leftrightarrow D$

| $C$ | $D$ | $C \leftrightarrow D$ |
| :-: | :-: | :-------------------: |
|  T  |  T  |           T           |
|  T  |  F  |           F           |
|  F  |  T  |           F           |
|  F  |  F  |           T           |

----
[Index](/README.md#sections) | [Next](/sections/formal_logic/equivalence.md)
