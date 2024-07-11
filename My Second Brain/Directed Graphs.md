---
tags: [logic]
Created: 2024-04-20T17:33:58+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A directed graph is like a [[Graphs|Graph]], except that the edges have a direction:
- A directed graph is a [[Relations#Irreflexivity|Irreflexive]] relation
- $G=(V,E)$ where $E\subseteq V\times V$ and $\forall v\in V(v,v)\not{\in} E$.
Due to directed graphs containing a directional attribute we are allowed to include both $(u,v)$ and $(v,u)$ as these are now counted as two separated edges.
![[Pasted image 20240420173308.png|centre|200]]

## Examples
- Sometimes airlines fly routes between three different cities in a cycle, so that their are direct flights one way, but not backwards
- Some roads are one-one. We can encode this into a directed graph for a road network
- We can form a dependency graph where the vertices are actions and $(u,v)$ is an edge if $u$ must be performed before $v$ can be performed. (e.g. you must put your socks on before your shoes)

# Directed Cycles
Much like how our graphs have cycles, our directed graphs have directed cycles. For example:
![[Pasted image 20240420174340.png|centre|250]]
$A,B,C,D,A$ would be a directed cycle. While $A,B,C$ is just a cycle.

# Directed Acyclic Graph
A directed acyclic graph or DAG is a directed graph which has no directed cycles:
![[Pasted image 20240420174529.png|centre|200]]
# Topological Ordering
Topological ordering is a total ordering $R$ on all the vertices of a directed graph $(V,E)$ where if there exists $(u,v)\in E$ then $uRv$. That is to say, a topological ordering is a total ordering $R$ on all vertices where $E\subseteq R$. Hence 

It's important to remember that not every directed graph allows for topological ordering. For example:
![[Pasted image 20240420174754.png|centre|200]]
## Relations
Due to topological orderings being a total orderings we must have the quality of transitivity $(\forall a,b,c\in A(aRb\land bRc)\to aRc)$. In the above graph we can see we have $aRb$ and $bRc$ however, we don't have $aRc$ instead we have $cRa$.

This relationship breaks our anti-symmetric relationship therefore no longer being a total ordering and by consequence a topological ordering. To allow for a topological ordering our directed graphs must not contain any directed cycles, that is to say that our directed graph is not acyclic.

