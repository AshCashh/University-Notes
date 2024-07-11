---
tags: [logic]
Created: 2024-04-15T18:18:44+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A graph $G$ is a pair $(V,E)$ where the set $V$ is the vertices or nodes of $G$ and the set $E\subseteq V\times V$ is the edges of $G$. For every $(u,v)\in E$, we also have $(v,u)\in E$ as well as there being no edges such that $(v,v)$. This means that graph shave an irreflexive, symmetric [[Relations|Relation]]. 

The graph described above is called a loop-free undirected graph which refers to its irreflexivity and symmetry.

# Visualisation
We generally visualise graphs as a set of points (vertices) connected by lines (edges). The arrangement of the vertices doesn't matter and can be chose arbitrarily. 
![[Pasted image 20240415182148.png|centre|300]]
An example of this including our notation could be:
$$V\in\{1,2,3\}\space E=\{(1,2),(2,1),(2,3),(3,2)\}$$

![[Pasted image 20240415182321.png|centre|200]]
# Definitions 
There are a few rules and definitions we can follow when it comes to graphs;
- If $(u,v)\in E$ then we can say that $u$ and $v$ are adjacent and are neighbours.
- The neighbourhood of a vertex $u$ is the set of $u$'s neighbours:
$$N_G(u)=\{v\in V:(u,v)\in E\}$$
- The neighbourhood of a set of vertices $S\subseteq V$ is the set of all neighbours of all vertices in $U$:
$$N_G(S)=\{v\in V:\exists u\in S,(u,v)\in E\}$$
- If $e=(u,v)\in E$ then we can say that $e$ is incident with $u$ and $v$.
- Due to our graphs being symmetric, that being for each $(u,v)\in E$ we also have $(v,y)\in E$, we can call these pairs the same edge and when counting they are considered as one.

## Graphs in Python
```python
V = {1,2,3,4,5}
E = { (1,2), (2,1), (2,3), (3,2), (3,1), (1,3), (1,4), (4,1), (4,5), (5,4)}
G = (V, E)

def N(V, E, u):
	# neighbourhood of a vertex u in graph (V, E)
	return {v for v in V if (u,v) in E }

def NS(V, E, S):
	# neighbourhood of a set of vertices S in graph (V, E)
	return {v for v in V for u in S if (u,v) in E }

print("Vertices", V) 
print("Edges", E) 
print("Neighbours of 1", N(G, 1)) 
print("Neighbours of {1,5}", NS(G, {1,5}))
```
# Graph Examples
- The set of all computers (including routers, hubs, etc) in a network, where u and v are adjacent if they are connected physically (say with Ethernet or Wifi)
- The set of cities in the world, where u is adjacent to v if there is a direct flight between u and v
- The set of all road intersections in the world, where u is adjacent to v if they are directly connected by a road

# Degrees
The degree of a vertex $u$ is the size of it's neighbourhood:
$$d(u)=|N_u|$$
Every edge $(u,v)$ adds 1 to the degree of $u$ and 1 to the degree of $v$, so we have:
$$2|E|=\sum\limits_{u\in V}d(u)$$
Since the sum of the degrees is even, that must mean that there is an even number of vertices with odd degrees. We call this the handshaking lemma.
"The number of people who have shaken an odd number of hands is even".

# Paths
A path is a sequence of vertices $v_1,v_2,\dots,v_j$ where:
- No vertex appears more than once
- $v_k$ is adjacent to $v_{k+1}$ for each $k=1,\dots, j-1$
- The length of the path is $j-1$ (the number of edges)

We can also say that an edge $(s,t)$ is in a path of $s=v_k$ and $t=v_{k+1}$ for some $k$.

# Cycles
A cycle is similar to a path however we start and end at the same place. This is equivalent to saying that $v_1=v_j$.
- The length of the cycle $j$ (the number of edges and number of vertices)
- Due to a cycle essentially being a loop, we don't care about which vertex is the starting point as $A,B,C,A$ is the same as $B,C,A,B$.
- Sometimes cycles don't duplicate the starting/ending vertex and instead just state "the cycle $A,B,C$" as opposed to "the path $A,B,C$".

# Connectedness
If there exists a path from $u$ to $v$ for every $u,v\in V$, then we can say that $G$ is connected. If this is false then we can say that $G$ is disconnected. We can also say that, if for every $u,v\in S\subseteq V$ there exists a path between $u$ and $v$ and there are no paths to any vertices outside of $S$, then $S$ is called a connected component of $G$.

# Distance
We can say that the distance between vertices $u$ and $v$ is the length of the shortest path from $u$ to $v$. If no such path exists then $d(u,v)=\infty$.  

## Calculating Distances
We can then calculate the distance by first fixing vertex $u$ in $V$. We can then define $D_j$ as the set of vertices that are of distance $j$ from $u$ and $V_j$ as the set of vertices that are of at least $j$ distance from $u$.
$$
V_j=
\begin{cases} \space V & : j=0\\
 \space V_{j-1}\backslash D_{j-1}& :j>1 \\
\end{cases}
$$
$$
D_j=
\begin{cases} \space \{u\} & : j=0\\
 \space N_{V_j}(D_{j-1})& :j>0 \\
\end{cases}
$$
For example:
![[Pasted image 20240415232427.png|centre|300]]
$$
\begin{align}
&D_0(A)\\
&V_0=V=\{A,B,C,D,E,F\}\\
&V_1=\{B,C,D,E,F\}\\
\\
&D_1(F)\\
&V_2=\{B,C,D,E\}\\
\\
&D_2(B,C)\\
&V_3=\{D,E\}\\
\\
&D_3(D,E)

\end{align}
$$
We can summarise the shortest path algorithm as:
- Set $D_0=\{u\}$ (starting vertex)
- Set $D_1=$ neighbours of $u$
- Set $D_2=$ neighbours of $d_1$ that we haven't seen before
- $\dots$

In this algorithm we process vertices and add them to some $D_j$ in order of distance where the closest vertices to $u$ come first.
# Bipartite Graphs 
A bipartite graph is a set of graph vertices split into two disjoint sets $(A,B)$ in such a way that no two graph vertices within the same set are adjacent. If this is the case $(A,B)$ can be called a bipartition of $G$. 

In the distance finding method we simply set $A=D_0\cup D_4\dots$ and $B=D_1\cup D_3\cup D_5\dots$. Then if no two vertices in the same distance set $(D_j)$ are adjacent we can call $(A,B)$ a bipartition of $G$. We can also say a graph $G$ is bipartite if and only if $G$ has no cycles of length.

## Matchings on Bipartite Graphs
A matching on a bipartite graph $G=(V,E)$ is a subset $M\subseteq E$ such that no vertex of $V$ is incident with more than one edge in $M$. A maximum matching on a graph is a matching such that no other matching on the graph has more edges. We can actually reduce the problem of finding maximum matchings to finding maximum flows. We can do this by following a four step process:
1. Add additional vertices $s$ and $d$.
2. Add edges $(s,a)\forall a\in A$
3. Add edges $(b,d)\forall b\in B$
4. Add weight 1 for every edge

# Sub-Graphs
A sub-graph is a smaller graph contained inside another graph. We can say the sub-graph of a graph $G=(V,E)$ is a graph $G'=(V',E')$ such that $V'\subseteq V$ and $E'\subseteq E$.

An induced sub-graph is a sub-graph $E'$ which contains all edges of $E$ that are incident with the vertices contained in $V'$. We write this as $G(V')$.
$$G(V'):=(V',\{(s,t)\in E:s,t\in V'\})$$
# Graphs Colourings
A $k$-colouring of a graph $G=(V,E)$ is a partition of $V$ into $k$ independent sets. The chromatic number of $G$ is the smallest integer $k$ for which $G$ has a $k$-colouring. For example, a bipartition is a 2-colouring. Bipartite graphs have chromatic number at most 2.

## 4 Colour Theorem

# Weighted Graphs
We can add additional information to graphs by using weights. In the context of edges, an example of adding weight to an edge may be giving it a label. We can do this by defining some function: $w:E\to\mathbb{R}$ ($\mathbb{R}$ can be replaced with things like $\mathbb{Z},\mathbb{N}$ or even another co-domain), where $E$ is our edge and $\mathbb{R}$ references the value associated with the edge. We can then say that for $e\in E$, the weight of $e$ is $w(e)$.

## Examples of Weights
- A graph of roads and intersections, with weights equal to the distance along a road between two intersections 
- A graph of network nodes and physical layer connections with weight equal to the bandwidth along a physical layer
- A graph of airports and directed flights, with weight equal to the cost of a seat on a flight
- A graph of roads and intersections, with weight equal to the capacity (cars per hour) of a road segment.

## Founded Information
- Find the lowest weight path between two vertices (weight of a path is the sum of the weights of the edge along the path).
- Find a minimum weight spanning spanning tree (weight of a tree is the sum of the weights of its edges)
- Find a maximum flow (maximum capacity of a graph between two vertices)

