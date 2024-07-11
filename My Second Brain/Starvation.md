---
tags: [cs, os]
Created: 2023-08-21T11:33:09+10:00
Modified: 2024-07-03T19:35:33+10:00
---
The implementation of a [[Mutex Locks & Semaphores#Semaphore Implementation|Semaphores]] with a waiting queue may result in a situation where two or more [[Process|Processes]] are waiting indefinitely for an event that can be caused only by one of the waiting processes. When such a state is reached, these processes are said to be deadlocked.

To illustrate this, consider a system of two processes $P_0$ and $P_1$, each accessing two semaphores $S$ and $Q$, set to the value 1:
![[Pasted image 20230821113659.png|centre|300]]
Now suppose that $P_0$ executes `wait(S)` and then $P_1$ executes `wait(Q)`. When $P_0$ executes `wait(Q)`, it must wait until $P_1$ executes `signal(Q)`. Similarly, when $P_1$ executes `wait(S)`, it also must wait until $P_0$ executes `signal(S)`. Since both these `signal()` operations cannot be executed, $P_0$ and $P_1$ are deadlocked.

# Starvation
Another major problem is indefinite blocking or starvation. Which is when a lower-priority process holds a lock needed by a higher priority process. In a heavily loaded system, a steady stream of higher-priority processes can prevent a low-priority process from ever getting the CPU.

A solution is aging, which involves gradually increasing the priority of processes that wait in the system for a long time.

# Priority Inversion
A scheduling challenge arises when a higher-priority process needs to read or modify kernel data that are currently being accessed by a lower-priority process - or a chain of lower-priority processes. The higher-priority process will have to wait for a lower-priority process one to finish with the resource, this situation becomes more complicated if the lower-priority process is preempted in favour of another process with a higher priority.

Typically priority inversion is avoided by implementing a priority-inheritance protocol. According to this protocol, all processes that are accessing resources needed by a higher-priority process inherit the higher priority until they are finished with the resources in question. When they are finished, their priorities revert to their original values.
