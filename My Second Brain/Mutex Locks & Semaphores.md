---
alias: Mutex Locks, Semaphores
tags: [cs, os]
Created: 2023-08-21T10:08:06+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Operating Systems]], designers build high-level software tools to solve the [[Process Synchronisation#Critical Section Problem|Critical Section Problem]]. The simplest of these tools is the Mutex Lock (where `mutex` is short for mutual exclusion). Designers use mutex lock to protect the critical section and thus prevent race conditions.

That is, a [[Process]] must acquire the lock (using the `aquire()` function) before entering a critical section and releases the lock when it exists (using the `release()` function). 
![[Pasted image 20230821101337.png|centre|300]]

A mutex lock has a boolean variable available whose value indicates if the lock is available or not. Calls to the `acquire()` and `release()` function **must be atomic** (cannot be interrupted mid execution) and are usually implemented via hardware atomic instructions.

The main disadvantage of such implementation is that it requires busy waiting, since a waiting to enter its critical section must loop continuously in the call to `aquire()`. This type of mutex lock is also called a **spin-lock** because the process "spins" while waiting for the lock to become available.

|          Acquire()          |          Release()          |
|:---------------------------:|:---------------------------:|
| ![[C Code Snippets#^acquire]] | ![[C Code Snippets#^release]] |

# Semaphores
A more robust tool that behaves very similar to [[Mutex Locks & Semaphores|Mutex Locks]] in solving the [[Process Synchronisation#Critical Section Problem|Critical Section Problem]], but can also provide more sophisticated ways for [[Process|Processes]] to synchronise their activities are semaphores.

A semaphore is an $S$ integer variable that is accessed only through two standard atomic operations `wait()` and `signal()`:

|          Wait()          |          Signal()          |
|:------------------------:|:--------------------------:|
| ![[C Code Snippets#^wait]] | ![[C Code Snippets#^signal]] |

All modifications to the $S$ variable in either operation must be executed atomically, that is, only one process can modify the value at a time.

## Semaphore Usage
OSs often distinguish between counting and binary semaphores. The value of a counting semaphore can range over an unrestricted domain. The value of a binary semaphore can range only between `0` and `1`. Thus, binary semaphores behave basically the same as mutex locks

## Semaphore Implementation 
With each semaphore there is an associated waiting queue, as it suffers (the same as mutex locks) from busy waiting. To overcome this problem, we can modify the definitions of the `wait()` and `signal()` operations as follows:
- When a process executes `wait()` and finds that the semaphore value is not positive, it must wait. However, the process can suspend itself
- The suspend operation places a process into a waiting queue associated with the semaphore.

A process can be placed in the waiting queue using the `block()` operation.
A process that is suspended, waiting on a semaphore can be restarted by a `wakeup()` operation, which changes the process from the waiting queue to the ready queue.

To implement semaphores under this definition, we define a semaphore to have an integer value and a list of processes list (waiting queue), where a pointer points to the next record.
```c
typedef struct{
	int value;
	struct process *list;
} semaphore;
```
Now the wait and signal operations can be modified as such:

|           WaitModified           | SignalModified |
|:--------------------------------:|:--------------:|
| ![[C Code Snippets#^WaitModified]] | ![[C Code Snippets#^SignalModified]]               |

However, this implementation can lead to [[Starvation|DeadLocks]].