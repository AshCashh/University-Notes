---
tags: [cs]
Created: 2023-08-14T21:34:43+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Support for [[Threads]] may be provided either at the user level, for user threads or by the kernel for kernel threads. User threads are supported above the kernel and are managed without kernel support, whereas kernel threads are supported and managed directly by the [[Operating Systems]].
The three primary thread libraries: POSIX Pthreads, Windows threads, Java threads.
![[Pasted image 20230814213949.png|centre|300]]
A relationship must exist between user and kernel threads. The three most common ways of establishing such relationships are: many-to-one, one-to-one, many-to-many model.

# Many-to-One Model
The many-to-one model maps many user-level threads to one kernel thread. Thread management is done by the thread library in user space, so it is considered efficient. However, the entire process will block if one thread makes a blocking system call. Also because only one thread can access the kernel at a time, multiple threads are unable to run in parallel on [[Threads#Multicore Programming|Multicore Systems]]. 
![[Pasted image 20230814214633.png|centre|300]]
Very few systems continue to use the model because of its inability to take advantage of multiple processing cores. Examples include: Solaris Green Threads, GNU Portable Threads.
# One-to-One Model
The one-to-one model maps each user thread to a kernel thread. It provides more concurrency than the many-to-one model by allowing another thread to run when a thread makes a blocking system call. The only drawback is that creating a user thread requires creating the corresponding kernel thread, hence a large of kernel threads may burden the performance of a system and be restricted due to overhead.
![[Pasted image 20230814215221.png|centre|300]]
Examples include: Windows, Linux and Solaris 9 and later.

# Many-to-Many Model
The many-to-many model multiplexes many user-level threads to a smaller or equal number of kernel threads. The number of kernel threads may be specific to either a particular application or a particular machine.
![[Pasted image 20230814215618.png|centre|300]]
Examples include: Prior version of Solaris 9 and Windows with the ThreadFiber package.

## Two-level Model
One variation to the many-to-many model except that it allows a user thread to be bound to a kernel thread.
![[Pasted image 20230814215954.png|centre|300]]
Examples include: IRIX, HP-UX, Tru64 UNIX