---
tags: [logic]
Created: 2024-04-23T11:37:51+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A flow network is a [[Directed Graphs]] where each edge has a capacity (weight) $w_e$ and a flow $f_e$. Each flow in the network contains a source and a drain and is bounded by 3 constraints:
1. The first constraint state that there exists no flow into the source and no flow out of the drain. 
2. The second constraint states that the flow on each edge cannot be a negative and must be less than the edges capacity 
3. The third constraint states that, excluding the source and drain, the flow value going into a vertex must be equal to the flow value going out of that vertex.
We can mathematically state the source of a flow as a function $f:E\to\mathbb{R}$ where $s\in V$ represents the source and $d\in D$ represents the drain. We can then state our 3 constraints as:
$1$:
$$\begin{align}
&\forall(u,s)\in E\space f((u,s))=0\\
&\forall (d.y)\in E\space f((d,u))=0\\
\end{align}
$$
$2$:
$$\begin{align}
0\leq f(e)\leq w(e)
\end{align}
$$
$1.$ $\forall v\in V\backslash \{s,d\}$:
$$\begin{align}
\sum\limits_{(u,v)\in E}f((u,v))=\sum\limits_{(v,u)\in E}f((v,u))
\end{align}
$$
where $(u,v)\in E$ represents the edges going into some vertex $v$ and $(v,u)\in E$ represents the edges going out of some vertex $v$. 

# Maximum Flows
So now that we know what a flow is we can start finding out some information about it. E.g. what happens if we want to find the maximum flow in our flow network.

We first define the value of a flow by the sum of flows coming out of the source.
$$\sum\limits_{(s,u)\in E}f((s,u))$$
And due to the conservation of flows the above is equal to the sum of flows into the drain:
$$\sum\limits_{(u,d)\in E}f((u,d))$$
The maximum flow problem on a weighted graph is to find the flow with highest flow value.

# Uses of Flows
Some uses:
- Find routing of data through a network to maximise bandwidth
- Determining the total capacity of a road network between two points
- Find capacity of an electric network to deliver power to a city 
- Determine optimal logistics for factories
Maximum flows are usually found using the [[Ford-Fulkerson Method]].

