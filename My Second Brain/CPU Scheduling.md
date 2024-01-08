#cs #os
CPU scheduling is the basis of multiprogrammed [[Operating Systems]]. By switching the CPU among [[Process|Processes]], the OS can make the computer more productive. 
# Basic Concepts
In a system with a single CPU core, only one process can run at a time. The objective of multiprogramming is to have some process running at all times, to maximise CPU utilisation. 

The success of CPU scheduling depends on an observed property of processes: process execution consists of a cycle of CPU execution and [[Input & Output|I/O]] wait. Processes alternate between these two states. Process execution begins with a **CPU burst**. That is followed by an **I/O burst**, followed by another CPU burst, and so forth. This is demonstrated below,
![[Pasted image 20230911124056.png|centre|300]]
The duration of CPU bursts are measured extensively. Although they vary greatly from process to process and from computer to computer. The CPU burst distribution is of main concern.
# CPU Scheduler
Whenever the CPU becomes idle, the OS must select one of the processes in the ready queue to be executed. This [[Process Scheduling]] is done by the CPU scheduler, which selects a process from the processes in memory that are ready to execute and allocates the CPU to that process.

CPU scheduling decisions may take place when a process switches from:
1. Running to waiting state
2. Running to ready state
3. Waiting to ready state
4. Or terminates
Situations under 1 and 4 are considered **non-preemptive** or cooperative. Otherwise it is **pre-emptive**:
- Consider access to shared data - can result in race conditions
- Consider preemption while in kernel mode
- Consider [[Interrupts]] occurring during crucial OS activities
# Dispatcher
Another component involved in the CPU-scheduling function is the dispatcher. The dispatcher is the module that gives control of the CPU's core to the process selected by the short term scheduler, this involves:
- Switching context
- Switching to user mode
- Jumping to the proper locations in the user program to resume that program.
The time it takes for the dispatcher to stop one process and start another running is know as the **dispatch latency**. 
# Scheduling Criteria
Different CPU-[[Scheduling Algorithms]] have different properties, and the choice of a particular algorithm may favour one class of processes over another. The following criteria have been suggested for comparing CPU scheduling algorithms:
- **CPU Utilisation**: Time in percentage when the cpu is busy. High = better
- **Throughput**: Number of processes that complete their execution per time unit
- **Turnaround Time**: Amount of time to execute a particular process
- **Waiting Time**: Amount of time a process has been waiting in the ready queue
- **Response Time**: Amount of time it takes from when a request was submitted until the the first response is produced, not output 
## Optimisation Criteria
Primary objects of a CPU scheduling algorithms:
- Max CPU utilisation, throughput
- Min turnaround time, waiting time, response time
