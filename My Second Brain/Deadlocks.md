#cs #os
In a multiprogramming environment, several [[Process|Processes]] may complete for a finite number of resources. A process requests resources; if the resources are not available at that time, the process enters a waiting state. Sometimes, a waiting process can never again change state, because the resources it has requested are held by other waiting processes. This situation is called a deadlock.
# System Model
A system consists of a finite number of resources to be distributed among a number of completing processes. Resources can consist of CPU cycles, memory space, [[Input & Output|I/O]] devices. But also [[Process Synchronisation|Synchronisation]] tools like [[Mutex Locks & Semaphores|Mutex Locks]], and [[Mutex Locks & Semaphores|Semaphores]]. A process must request a resource before using it and must release the resource after using it. Under the normal mode of operation, a process may utilise a resource in only the following sequence:
1. **Request**: The process requests the resource. If it cannot be granted, it must wait.
2. **Use**: The process can operate on the resource
3. **Release**: The process releases the resource
# Deadlock Characterisation
Deadlocks can arise if four conditions hold simultaneously in a system:
1. **Mutual Exclusion**: Only one process at a time can use a resource
2. **Hold and Wait**: A process must be holding at least one resource and waiting to acquire additional resources held by other processes
3. **No Preemption**: A resources can be released only voluntarily by the process holding it, after that process has completed its task
4. **Circular Wait**: A set $(T_0,T_1,\dots,T_n)$ of waiting processes must exist such that $T_0$ is waiting for a resource held by $T_1$, $T_1$ is waiting for a resource held by $T_2$ $\dots$, $T_{n-1}$ is waiting for a resource held by $T_n$, and $T_n$ is waiting for a resource held by $T_0$.
We emphasise that all four conditions must hold for a deadlock to occur.
## Resource-Allocation Graph
Deadlocks can be described more precisely in terms of a directed graph called a system resource-allocation graph. This graph consists of a set of vertices $V$ and a set of edges $E$. The set of vertices $V$ is partition into two types:
- $T=(T_1,T_2,\dots,T_n)$, the set consisting of all active processes in the system
- $R=(R_1,R_2,\dots,R_m)$, the set consisting of all resource types in the system
A directed edge $T_i\to R_j$ is called a **request edge**.
A directed edge $R_j\to T_i$ is called an **assignment edge**.
### Viable Behaviour Example
![[Pasted image 20230914232033.png|centre|300]]
$$E=\{T_1\to R_1,T_2\to R_3,R_1\to T_2,R_2\to T_2,R_2\to T_1,R_3\to T_3\}$$
Resource instances: 
- One instance of resource type $R_1$
- Two instances of resource type $R_2$
- Three instances of resource type $R_4$
Thread states:
- Thread $T_1$ is holding an instance of resource type $R_2$ and is waiting / requesting for an instance of resource type $R_1$
- Thread $T_2$ is holding an instance of $R_1$ and an instance of $R_2$ and is waiting / requesting for an instance of $R-3$
- Thread $T_3$ is holding an instance of $R_3$
### Deadlock Example
![[Pasted image 20230914232755.png|centre|300]]
Because of the edge $T_3\to R_2$, two minimal cycles exist within the system. Threads $T_1, T_2$ and $T_3$ are deadlocked. Since $T_2$ is waiting for the resource of $R_3$, which is held by thread $T_3$. Thread $T_3$ is waiting for either thread $T_1$ or $T_2$ to release resources $R_2$. In addition, $T_1$ is waiting for thread $T_2$ to release $R_1$.
### Cycle But No Deadlock Example
![[Pasted image 20230914233306.png|centre|300]]
There is no deadlock here because $T_4$ may release its instance of resource type $R_2$. That resource can then be allocated to $T_3$, breaking the cycle.
### Basic Facts
- If a graph contains no cycles $\to$ no deadlock
- If a graph contains a cycle:
	- If only one instance per resource type, then deadlock
	- If several instances per resource type, possibility of deadlock
# Methods for Handling Deadlocks
Generally speaking, we can deal with the deadlock problem in one of three ways:
- Implement a protocol to ensure that the system will *never* enter a deadlocked state
- Allow the system to enter a deadlocked state, detect it and recover
- Ignore the problem and pretend that deadlocks never occur in the system; used by most OS, including UNIX.
# Recovery from Deadlock
When a detected algorithm determines that a deadlock exists, several alternatives are available. Either abort all deadlocked processes or abort one process at a time until the deadlock cycle is eliminated.

In which order should we choose to abort?
1. Priority of the process
2. How long process has computed, and how much longer to completion
3. Resources the process has used
4. Resources process needs to complete
5. How many processes will need to be terminated
6. Is process interactive or batch

## Resource Preemption
To eliminate deadlocks using resource preemption, we successively preempt some resources from processes and give these resources to other processes until the deadlock cycle is broken.

If preemption is required to deal with deadlocks, then three issues need to be addresses:
1. Selecting a victim: Which resources and which processes are to be preempted? Minimise cost 
2. Rollback: Return to some safe state, restart process for that state
3. Starvation: Same process may always be picked as victim, include number of rollback in cost factor