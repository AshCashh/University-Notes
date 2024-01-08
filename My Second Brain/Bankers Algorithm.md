#os
The [[Deadlock Prevention,Avoidance#Resource Allocation Graph Scheme|Resource-Allocation Graph]] algorithm is not applicable to a resource-allocation system with multiple instances of each resource type. Hence the banker's [[Algorithm]] is used. The name was chosen because the algorithm could be used in a banking system to ensure that the bank never allocated its available cash in such a way that it could no longer satisfy the needs of its customers.
- Each [[Process]] must a priori claim its maximum use (number of instances)
- When a process requests a resource it may have to wait
- When a process gets all its resources it must return them in a finite amount of time
# Data Structures
Several data structures must be maintained to implement the banker's algorithm. The following are needed, where $n$ is the number of process and $m$ is the number of resource types:
- **Available**: A vector of length $m$. If $\text{Available}[j]=k$, then $k$ instances of type $R_j$ are available
- **Max**: An $n\times m$ matrix defines the maximum demand of each process. If $\text{Max}[i][j]=k$, then process $P_i$ may request at most $k$ instances of resource type $R_j$
- **Allocation**: An $n\times m$ matrix defines the number of resources of each type currently allocated. If $\text{Allocation}[i][j]=k$, then process $P_i$ is currently allocated $k$ instances of resource type $R_j$
- **Need**: An $n\times m$ matrix indicates the remaining resource need of each process. If $\text{Need}[i][j]=k$, then process $P_i$ may need $k$ more instances of $R_j$ to complete its task.
$$\text{Need}[i][j]=\text{Max}[i][j]-\text{Allocation[i][j]}$$
## Safety Algorithm
We can now present the algorithm for finding out whether or not a system is in a [[Deadlock Prevention,Avoidance#Safe State|Safe State]]. This can be described as:
1 .Let **Work** and **Finish** be vectors of length $m$ and $n$, respectively. Initialise:
```c
Work = Available
Finish[i] = false for i = 0,1,...,n-1
```
2. Find an index $i$ such that both:
```c
Finish[i] == false
Need_i <= Work
```
If no such $i$ exists, go to 4.
3. Complete
```c
Work = Work + Allocation_i
Finish[i] = true
```
Go to step 2.
4. If 
```c
Finish[i] == true for all i
```
Then the system is in a safe state.

## Resource-Request Algorithm
Next, we describe the algorithm for determining whether requests can be safely granted.

Let $\text{Request}_i$ be the request vector for process $P_i$. If $\text{Request}_i[j]=k$ then process $P_i$ wants $k$ instances of resource type $R_j$. When a request for resources is made by thread $P_i$, the following actions are taken:
1. If $\mathbf{Request}_i\leq \mathbf{Need}_i$, go to step 2. Otherwise, raise error condition, since the process has exceeded its maximum claim.
2. If $\mathbf{Request}_i\leq\mathbf{Available}$, go to step 3. Otherwise $P_i$ must wait, since the resources are not available
3. Have the system pretend to have allocated the requested resources to process $P_i$ by modifying the state as follows:
$$\begin{align*}
\mathbf{Available}&=\mathbf{Available}-\mathbf{Request}_i\\
\mathbf{Allocation}_i&=\mathbf{Allocation}_i+\mathbf{Request}_i\\
\mathbf{Need}_i&=\mathbf{Need}_i-\mathbf{Request}_i
\end{align*}$$
If the resulting resource allocation state is safe, $P_i$ is allocated its resources. 
If if the new state is unsafe, then $T_i$ must wait and the old resource allocation state is restored.

## Example
![[Pasted image 20230917214457.png]]
