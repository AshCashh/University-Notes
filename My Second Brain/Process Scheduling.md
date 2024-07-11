---
tags: [cs, os]
Created: 2023-08-04T21:20:30+10:00
Modified: 2024-07-03T19:35:33+10:00
---
The objective of multiprogramming is to have some [[Process]] running at all times so as to maximise CPU utilisation. A process scheduler is used to determine which process should be executed. The number of processes currently in memory is known as the degree of multiprogramming

As processes enter the system they are put into a **ready queue**, where they wait to execute on a CPU's core. This queue is generally stored as a linked list; a ready-queue header contains pointers to the first PCB in the list. When a process enters the system, it's put into a **ready queue** where it then waits to be executed. When a process is allocated a CPU core for execution it executes for a while and eventually terminates, is interrupted or waits for the occurrence of a particular event. Any process waiting for an event to occur gets placed into the **wait queue**. 
![[Pasted image 20230804212521.png|centre|500]]

Most processors can be described as either:
- I/O bound: A I/O bound process that spends more of its time doing I/O operations
- CPU bound: Spends more of its time doing more calculations with infrequent I/O requests

# Schedulers
As stated schedulers select available processes for program execution on a core. These schedulers consist in three magnitudes; long-term, medium-term and short-term:

**Long-Term Scheduler (job scheduler)**: Selects which processes should be brought into the ready core.
- It's invoked very infrequently (seconds, minutes)
- Controls the degree of multiprogramming
- Strives for good process mix

**Short-Term Scheduler (CPU scheduler):** Selects which process should be executed next and allocates CPU.
- It's invoked very frequently (milliseconds)
- Sometimes is the only scheduler in a system

Medium-Term Scheduler: Can be added if degree of multiple programming needs to decrease.
- Removes process from memory, store on disk, bring back in from disk to continue execution (swapping)

# Context Switch
[[Interrupts]] cause the [[Operating Systems]] to change a CPU core from its current task and to run a kernel routine. When this switch happens the system needs to save the state of the old process and load the saved state for the new process via a context switch. Context-switch time is pure overhead, so the system does no useful work while switching and the more complex the OS and PCB, the longer the context switch.

Context-switch times are highly dependent on hardware support, some hardware provides multiple sets of registers per CPU and hence will have multiple contexts loaded at once.
![[Pasted image 20230805081747.png|400]]