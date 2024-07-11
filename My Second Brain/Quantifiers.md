---
aliases:
  - Quantification
  - Quantifier
tags: [logic]
Created: 2024-03-25T21:47:41+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Quantifiers are symbols that allow us to give some information about the parameters used in [[Predicate Logic|Predicates]]. Quantifiers are useful as they allow us to form propositions out of predicates without the need to define a boolean value for their parameters. There are two kinds of quantifiers:
1. **Existential Quantification** $\exists$ : Used to say something exists.
2. **Universal Quantification** $\forall$ : Used to say something about all of a certain value.

When we use a quantifier we always need to specify which set our values are coming from and if not we must specify with context which universe our values come from.

## Universal Quantification
The universal quantifier on the other hand is used to say "for all" and is represented by the symbol $\forall$. For example, say we wanted to write that for every $x\in\mathbb{Z},x^2$ is a non-negative. We can do so as such using our universal quantifier:
$$\forall x\in \mathbb{Z}(x^2\geq 0)$$
For this example, it doesn't matter which value from $\mathbb{Z}$ we use to fill in our predicate, we will always get a true statement.

#### Examples
- $\forall x \in S\space p(x)$ means: For all $x$ from $S$, $p(x)$ is true.
- $\forall x\in$ ANIMALS ($x$ is a cat) means: For all $x$ in ANIMALS, x is a cat.
- $\forall x\in\mathbb{Z}(x\in\mathbb{R})$ means: All integers are real numbers 

### Truth Table
When we universally quantify over finite sets we have to check **all values** in the set to determine if the predicate is **true** (fully quantifiable). For example:
$$\forall x\in\{0,1\}(x^2=x)$$
is true because $0^2=0$ and $1^2=1$

But to show that it is **false**, we just need to find **one value that is false** (doesn't work).
$$\forall x\in\{0,1\}(x^2=1)$$
is false because $0^2\neq 1$. 
## Existential Quantification
The existential quantifier is used to say "there exists" and is represented by the $\exists$ symbol. For example, say we wanted to write that there exists a value $x\in\mathbb{Z}$ where $x^2=4$. We can write that using our existential quantifier as such:
$$\exists x\in\mathbb{Z}(x^2=4)$$
This doesn't tell us what $x$ actually represents, just that there exists some value $x$ that matches our condition.

#### Examples
- $\exists x \in S\space p(x)$ means: There exists an $x$ in $S$ such that $p(x)$ is true
- $\exists x\in$ ANIMALS $x$ is a fish means: There exists an $x$ in ANIMALS such that $x$ is a fish
- $\exists x\in\mathbb{R}(x\in\mathbb{Z})$ means: There exists some real number $x$ such that $x$ is an integer 

### Truth Table
For existential quantifiers, we only need to find **one value** that is works to show something is **true** (fully quantifiable).
$$\exists x\in\{0,1\}(x^2=1)$$
is true because $1^2=1$

But to show that it is **false**, we need to check **every value**:
$$\exists x \in \{0,1\}(x^2=2)$$
is false because $0^2\neq 2$ and $1^2\neq 2$.

# Order of Quantifiers
If there are multiple quantifiers of different types, then the order matters. With universe $\mathbb{Z}$:
$$\forall y\exists x(x+y=0)$$
is true. For any y we can use the value $x=-y$. But:
$$\exists x \forall y(x+y=0)$$
is false. For any value x we can choose $y=x+1$ so $x+y=1\neq 0$.

## Boolean Formulas
Suppose $A(x,y)$ is a Boolean formula with $x$ and $y$ some propositions. Then:
- $A$ is a tautology means $\forall x,y A(x,y)$
- $A$ is a contradiction means $\forall x, y\neg A(x,y)$
- $A$ is satisfiable means $\exists x, yA(x,y)$