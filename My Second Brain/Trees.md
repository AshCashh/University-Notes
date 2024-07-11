---
aliases:
  - Tree
tags: [cs]
Created: 2024-04-20T11:25:36+10:00
Modified: 2024-07-03T19:29:11+10:00
---
A tree is a connected [[Graphs|Graph]] that does not include cycles. Some important things to note about trees is that:
- A tree will always have $|V|-1$ edges
- There will always be a unique path between any two vertices
We call a graph that has disconnections without any cycles a forest. In these types of graphs each connected component is a tree.
![[Pasted image 20240420113009.png|centre|400]]
# Rooted Trees
In a tree graph we can identify a special vertex as the root. This allows us to gain some additional organisation to our tree graph.
- The parent of the vertex is the first vertex in the unique path to the root
- The ancestors of a vertex is its parent, it's parent's parent and so on until we reach the root
- The root vertex has no parents
- Any vertex in our graph can be the root therefore we must specify it
- We call the parent of $v$, $P(v)$

# Recursive Definition of Ancestors
Let's say we have vertex $v$, we would then call all ancestors of $v$, $A(v)$.
- If $v$ is the root then $A(v)=\emptyset$ 
- If $v$ is no the root then $A(v)=\{P(v)\}\cup A(P(v))$
In the image above, the root is chosen to be $A$, where $B$'s ancestors are $A$ and $D$'s ancestors are $A$ and $B$. 

We can also say that:
- A vertex's children are all of its neighbours excluding its parent
- All descendants of a vertex are considered its children, all of its children's children and so on
- We call a vertex without children a leaf

# Recursive Definition of Descendants
Let's say we have vertex $v$, we would then call the set of children of $v$, $C(v)$ and the set of descendants $D(v)$.
- If $v$ is the root then $C(v)=N_v$ otherwise $C(v)=N_v\backslash\{P(v)\}$ 
We can calculate the descendants by:
$$D(v)=C(v)\cup\bigcup_{u\in C(v)}D(u)$$
So using the same image as above: $A$'s children are $C$ and $B$. $B$'s descendants are $E$ and $D$. The leaves are $C,E$ and $D$.

# Sub-Trees
If we have a rooted tree, we can then define sub-trees as:
- A sub-tree of a rooted tree on vertex $V$ is the induced sub-graph on $v$ and its descendent
- A sub-tree will always be a rooted tree, in this instance $v$ is the root

