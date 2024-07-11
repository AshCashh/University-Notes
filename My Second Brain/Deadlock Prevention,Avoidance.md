---
tags: [os, cs]
Created: 2023-09-17T17:23:41+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# [[Deadlocks|Deadlock]] Prevention
**Mutual Exclusion**:
The mutual exclusion condition must hold. That is, at least one resource must be non-sharable. Sharable resources do not require mutually exclusive access and thus cannot be involved in a deadlock. Read-only files are a good example of sharable resources.
**Hold and Wait**:
Must guarantee that whenever a process requests a resource, it does not hold any other resources. 
- Require a process to request and be allocated all its resources before it begins execution, or allow process to request resources only when the process has none
Low resource utilisation means [[Starvation]] is possible.
**No Preemption**:
If a [[Process]] is holding some resources and requests another resource that cannot be immediately allocated to it, then all resources currently being held are released. Preempted resources are added to the list of resources for which the process is waiting. Process will be restarted only when it can regain its old resources, as well as the new ones that it is requesting.
**Circular Wait**:
Impose a total ordering of all resource types, and require that each process requests resources in an increasing order of enumeration (best solution for simple systems).
# Deadlock Avoidance
Requires that the system has some additional **a priori** information available:
- Simplest and most useful model requires that each process declare the **maximum number** of resources of each type that it may need.
- The deadlock-avoidance algorithm dynamically examines the resource-allocation state to ensure that there can never be a circular-wait condition
- Resource-allocation state is defined by the number of available and allocated resources, and the maximum demands of the processes
## Safe State
A state is *safe* if the system can allocate resources to each process (up to its maximum) in some order and still avoid a deadlock. Systems is in safe state if there exists a sequence of processes $(P_1,P_2,\dots,P_n)$ of ALL the processes in the system such that for each $P_i$, the resources that $P_i$ can still request can be satisfied by currently available and resources held by all the $P_j$ with $j<i$.

That is:
- If $P_i$ resource needs are not immediately available, then $P_i$ can wait until all $P_j$ have finished
- When $P_j$ is finished, $P_i$ can obtain needed resources, execute, return allocated resources and terminate
- When $P_i$ terminates, $P_{i+1}$ can obtain its needed resources and so on.

Basic Facts:
- If a system is in safe state $\to$ no deadlocks
- If a system is in unsafe state $\to$ possibility of deadlocks
- Avoidance $\to$ ensure that a system will never enter an unsafe state
# Avoidance Algorithms
Single instance of a resource type:
- Use a resource-allocation graph
Multiple instances of a resource type:
- Use the [[Bankers Algorithm]]
## Resource Allocation Graph Scheme
- Claim edge $P_i\to R_j$ indicated that process $P_i$ may request resource $R_j$; represented by a dashed line. 
- Claim edge converts to request edge when a process requests a resource. 
- Request edge convert to an assignment edge when the resource is allocated to the process
- When a resource is released by a process, assignment edge reconverts to claim edge
- Resources must be claimed a priori in the system.
![[Pasted image 20230915114027.png|centre|300]]
![[Pasted image 20230915114058.png|centre|300]]
