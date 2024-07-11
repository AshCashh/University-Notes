---
aliases:
  - Relation
tags: [logic, math]
Created: 2024-04-02T14:18:53+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Mathematics]], a relation on a [[Set Theory|Set]] may or may not hold between two given members of the set. As an example, "is less than" is a relation on the set of natural numbers.

A relation is a fixed length collection of tuples where each entry of the [[Tuple]] is taken from a set.
- A relation on $A_1\dots A_n$ is a subset of $A_1\times\dots A_n$
- A binary relation between $A$ and $B$ is a subset of $A\times B$
- A binary relation between $A$ and $A$ is called a relation over $A$
### Examples
- $\{(1,1),(2,2)\}$
- $\{(a,b)\in\mathbb{R}^2:a=b\}$ (equality)
- $\{(a,b)\in\mathbb{Z}^2:\exists c\in\mathbb{Z}a=bc\}$
- $\leq,<,=,\geq,>$ 

# Properties
We can identify special properties that some binary relations will have:
## Symmetric
We say that a binary relation $R\subseteq A\times A$ is symmetric if:
$$
\forall a,b\in A\times A(aRb\leftrightarrow bRa)
$$
where $aRb$ means that $(a,b)\in R$. Hence saying that whenever we have $(a,b)$ we also have $(b,a)$.
### Examples
- $=$
- $a\equiv b$ (mod n) (equivalence modulo $n$)
- $\emptyset,A\times A$ (i.e. the trivial relations)

## Anti-Symmetric
A binary relation $R\subseteq A\times A$ is anti-symmetric if:
$$\forall x,y\in A((xRy\land yRx)\to x=y)$$
or, using the contrapositive:
$$\forall x,y\in A(x\neq y\to\neg(xRy\land yRx))$$
In other words, if $x$ and $y$ are different then we can't have both $xRy$ and $yRx$
### Examples
- $<,>$
- $\leq,\geq$
- $\subset, \subseteq$

## Reflexivity
A binary relation $R\subseteq A\times A$ is reflexive if:
$$\forall a\in A \space aRa$$
### Examples
- $\leq, \geq$
- $=$
- $\subseteq$
- $a\equiv b\space\text{(mod n)}$

## Irreflexivity
We that a binary relation $R\subseteq A\times A$ is irreflexive if:
$$\forall x\in A(x,x)\not{\in} R$$
### Examples
- $<,>$
- $\subset$
- $\neq$

## Transitivity
We say a relation $R\subseteq A\times A$ is transitive if:
$$\forall a,b,c\in A((aRb\land bRc)\to aRc)$$
### Examples
- $\leq,<,=,\geq,>$
- $\subset,\subseteq$
- $a\equiv b\space\text{(mod n)}$
# Equivalence Relations
An equivalence relation $R$ over a set that is **symmetric**, **reflexive** and **transitive**. An equivalence relation $R\subseteq A\times A$ separates a set into equivalence classes. These are subsets of $A$ that are all related by the relation. For example, the equivalence relation given by $a\equiv b$ (mod 2) gives two equivalence classes, the even and odd numbers.

# Partial Orderings 
A partial ordering on a set $A$ is a binary relation over $A$ which is **reflexive**, **transitive**, **anti-symmetric**. Partial orderings allow us to capture the idea of one thing coming before another. If the relation is irreflexive then we call it a strict partial ordering.
### Examples
- $\leq,\geq, \subseteq$

# Total Orderings
A total ordering on a set $A$ is a partial ordering $R$ over $A$ that also has the property:
$$\forall x,y\in A(xRy\lor yRx)$$
This means that we can always compare any two elements of $A$.
### Examples
- $\leq,\geq$
- [[Encoding#Lexicographic Ordering]]
If the relation is irreflexive instead of reflexive, it is called a struct total ordering.

# Relations Examples
## Ancestry
Let $H$ be the set of all humans. Define $R$ over $H$ by $aRb$ if $b$ is an ancestor of $a$. i.e. $b$ is a parent, grandparent, great-grandparent, etc. of $a$.

Is $R$:
- Symmetric: No but is anti-symmetric.  
- Transitive: Yes 'the ancestor of a ancestor is an ancestor'.
- Reflexive: No 'am I an ancestor to myself'.
- Irreflexive: Yes
- An equivalence relation: No
- Partial Ordering: Yes
- Total Ordering: No

## Marriage
Let $H$ be the set of all humans in Australia. Define $R$ over $H$ by $aRb$ if $a$ is married to $b$.

Is $R$:
- Symmetric: Yes, a is married to be and so is b to a.
- Anti-Symmetric: No
- Transitive: No
- Reflexive: No, not married to yourself
- Irreflexive: Yes, nobody is married to themselves
- An equivalence relation: No
- Partial ordering / Total ordering: No

## City Location
Let $S$ be the set of all cities in Australia. Define $R$ over $S$ by $aRb$ if $a$ is south of $b$ or at the same latitude as $b$.
Is $R$:
- Symmetric: No
- Anti-symmetric: Yes
- Transitive: Yes, Sydney is south of brisbane, brisbane is south of townsvill, hence sydney is south of Townsvill
- Reflexive: Yes because every city is at the same latitude as itself
- Irreflexive: No
- An equivalence relation: No
- Partial Ordering: Yes, is anti-sym, transitive, reflexive
- Total ordering: Yes

## 3 Hashes
Let $S$ be the set $\{0,1\}^*$ of bit strings of any length and let $H(x)$ be the SHA256 hash$^*$ of $x$. Define $R$ over $S$ by $aRb$ if $H(a)=H(b)$.
Is $R$:
- Symmetric: Yes has equality $=$
- Anti-symmetric: No
- Transitive: Yes
- Reflexive: Yes
- Irreflexive: No
- An equivalence relation: Yes
- Partial Ordering / Total Ordering: No
Equivalence classes: Same thing that hash to the value, defined as collision.

$$ \forall a,b\in V,|N(a)\cap N(b)|\geq 2$$
$$\forall a,b\in V, d(a)=d(b)$$