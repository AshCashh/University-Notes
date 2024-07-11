---
tags: [cs]
Created: 2023-08-14T12:58:19+10:00
Modified: 2024-07-03T19:31:57+10:00
---
A thread is a basic unit of CPU utilisation; it comprises a thread ID, a program counter (PC), a register set, and a stack. It shares with other threads belonging to the same [[Process]] its code section, data section and other [[Operating Systems]] resources, such as open files and signals. A traditional process has a single thread of control. If a process has multiple threads of control, it can perform more than one task at a time.
![[Pasted image 20230814130201.png|centre|500]]
# Motivation
Most software applications that run on modern computers are multithreaded. An application typically is implemented as a separate process with several threads of control. Examples of multithreaded applications include:
- Web browser might have one thread display images or text while another thread for retrieving data from the network
- A word processor may have threads for displaying graphics, another for responding to keystrokes from the user, or performing spelling and grammar checking.

Most OS kernels are multithreaded, during system boot on Linux, several kernel threads are created. Each will perform a specific task like managing devices, memory management or interrupt handling. The command `ps -ef` can be used to display the kernel threads.

Many applications will take advantage of multiple threads, including basic sorting, trees and graphic algorithms. In addition, programmers whom solve CPU intensive problems in data mining, graphics, and AI can leverage the power of multicore systems by designing solutions that run in parallel.

# Threading Benefits
The benefits of multithreaded programming can be broken down into four major categories:
1. **Responsiveness**: May allow continued execution if part of a process is blocked, especially important for user interface
2. **Resource Sharing**: Threads share resources of process, easier than shared memory or message passing
3. **Economy**: Cheaper than process creation (is preferred over processes for background applications), thread switching has lower overhead than context switching (is faster)
4. **Scalability**: Process can take advantage of multiprocessor architectures

# Threading Issues
The semantics of the `fork()` and `exec()` system calls change in a multithreaded program. Some UNIX systems have specifically chosen to have two versions of `fork()`, one that will duplicate all threads and another that duplicates only the thread that invoked the `fork()` call. If a thread invokes the `exec()` system call, the program specified in the parameter to `exec()` will replace the entire process - including all threads.

Which of the two versions of `fork()` to use depends on the application and if `fork()` is called immediately after forking, then duplicating all threads is unnecessary.

A signal may be received either synchronously or asynchronously, depending on the source of and the reason for the event being signaled. This is to be considered greatly when designing multithreaded programs.

Thread cancellation involves terminating a thread before it has completed, often referred to as the target thread. Cancellation may occur in two different scenarios: 
- Asynchronous cancellation: Terminates the target thread immediately
- Deferred cancellation: Allows the target thread to periodically check if it should be cancelled.
# Multicore Programming
Multicore or multithreaded programming provides a mechanism for more efficient use of these multiple computing cores and improved concurrency. However, it does place pressure on system designers and application programmers to make better use of multiple computing cores. 
In general, give areas present challenges in programming for multicore systems:
1. Dividing activities
2. Balance
3. Data splitting
4. Data dependency
5. Testing and debugging

A concurrent system supports more than one task by allowing all the tasks to make progress. In contrast, a parallel system can perform more than one task simultaneously. Thus, it is possible to have concurrency without parallelism.
## Types of Parallelism
Parallelism implies a system can perform more than one task simultaneously. In general there are two types of parallelism:
1. Data Parallelism: Focuses on distributing subsets of the same data across multiple computing cores and performing the same operation on each core.
2. Task Parallelism: Focuses on distributing threads across multiple cores, each thread performing a unique operation.

As the number of threads grow, so does architectural support for threading. CPUs have cores as well as hardware threads.

# Thread Scheduling
On most modern OSs it is kernel-level threads that are being scheduled by the OS and not processes. User-level threads are managed by a thread library and the kernel is aware of them. To run on a CPU, user-level threads must be mapped to an associated kernel-level thread.

One distinction between user-level and kernel-level threads lies in how they are scheduled. In systems implementing the [[Multithreading Models#Many-to-One Model|Many-To-One]] and Many-To-Many models, the thread library schedules user-level threads to run on available LWP. This is known as **process contention scope** (PCS), since competition for the CPU takes place among threads belonging to the same process. To decide which kernel-level thread to schedule onto a CPU, the kernel uses **system contention scope** (SCS). Competition for the CPU with SCS scheduling takes place among all threads in the system.