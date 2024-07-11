---
alias: Synchronisation
tags: [cs, os]
Created: 2023-08-20T18:40:12+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Since, [[Process|Processes]] can execute concurrently via [[Process Scheduling]], quite often processes may be interrupted and only partially complete execution before another process is scheduled. Here, we will explain how concurrent access to shared data may result in [[Problems of Synchronisation]], and how ensuring the orderly execution of cooperating processes resolves such issues.

To illustrate the problem, suppose we wanted to provide a solution to the [[Inter-Process Communication#IPC in Shared-Memory Systems|Consumer-Producer Problem]] that fills all the buffers. We can do so by having an integer `counter` that keeps track of the number of full buffers. Initially the `counter` is 0 and is incremented by the producer after a new buffer and decremented by the consumer after it consumes a buffer.

|          Producer          | Consumer |
|:--------------------------:|:--------:|
| ![[C Code Snippets#^ProducerProcess]] | ![[C Code Snippets#^ConsumerProcess]]         |

Although the producer and consumer routines shown above are correct separately, they may not function as expected when executed concurrently:
![[Pasted image 20230820222649.png]]

Notice that we have arrived at the incorrect state `counter = 4`, when in fact, 5 buffers are full not 4. This situation occurred because both processes were manipulating the variable `counter` concurrently.

This situation where several processes can access and manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place, is called a **race condition**. To guard against the race condition, only one process at a time can be manipulating the variable `counter`, and therefore must be synchronised with other processes.

# Critical Section Problem
Consider a system consisting of $n$ processes $\{P_0,P_1,\dots,P_{n-1}\}$. 
Each process has a segment of code, called a critical section:
- Process may be changing common variables, updating data that is shared with at least one process.
- When executing in its critical section, no other process is allowed to execute in its critical section.
- Hence, no two processes are executing in their critical sections at the same time.
The critical section problem is designed such that each process must **request permission** to enter its critical section, which is the **entry section**. The critical section may be followed by an exit section. The remaining code is called the remainder section.
![[Pasted image 20230820232438.png|centre|300]]

A solution to the critical-section problem must satisfy the following requirements:
1. **Mutual Exclusion**: If process $P_i$ is executing in its critical section, then no other processes can be executing in their critical section.
2. **Progress:** If no process is executing in its critical section and some processes wish to enter their critical sections, then the selection of the processes that will enter the critical section next cannot be postponed indefinitely
3. **Bounded Waiting:** A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its own critical section and before that request is granted:
	- Assume that each process executes at a nonzero speed
	- No assumption concerning relative speed of the $n$ processes

Two general approaches are used to handle critical sections depending on if kernel is preemptive or non-preemptive:
- **Preemptive:** Allows preemption of process when running kernel mode
- **Non-Preemptive:** Runs until it exits kernel mode, blocks or voluntarily yields control of the CPU
A nonpreemptive kernel is essentially free from race conditions in kernel mode, and hence not typically implemented.

# Peterson's Solution
One software-based solution to the critical section problem is known as the Peterson's solution. The solution is restricted to two processes that alternate execution between their critical sections and remainder sections. The two processes share two data items:
```c
int turn;
boolean flag[2];
```
The variable `turn` indicates whose turn it is enter its critical section. The flag array is used to indicate if a process is ready to enter the critical section. `flag[i] = true` implies that process $P_i$ is ready to enter its critical section.

|Process 1           | Process 2           |
| :-------------------: | :-------------------: |
| ![[C Code Snippets#^Process1]] | ![[C Code Snippets#^Process2]] |

Here, the value of turn will determine which of the two processes is allowed to enter its critical section first.

```dataview 
CALENDAR file.ctime 
```


```dataview

TABLE
file.ctime as Created
FROM #ee
SORT file.time ASC
```

