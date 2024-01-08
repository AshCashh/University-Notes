#cs #os
[[CPU Scheduling]] deals with the problem of deciding which of the [[Process|Processes]] in the ready queue is to be allocated the CPU's core. There are many different CPU scheduling algorithms, although most modern CPU architectures have multiple processing cores, these are described in the context of only one processing core.

# First-Come, First-Served Scheduling
By far the simplest algorithm is the first-come first-serve (FCFS) algorithm. With these scheme the process that requests the CPU first is allocated the CPU first.

| Process | Burst Time |
|:-------:|:----------:|
|  $P_1$  |   24         |
|  $P_2$  |  3          |
|  $P_3$  | 3           |

If the processes arrive in the order $P_1,P_2,P_3$ and are served in FCFS order, we get the results shown below, 
![[Pasted image 20230911130959.png]]

The waiting time is 0 milliseconds for process $P_1$, 24 milliseconds for $P_2$, etc.
The average waiting time is: $(0+24+27)/3=17$ milliseconds.

Now suppose the processes arrive in the order $P_2,P_3,P_1$
![[Pasted image 20230911131242.png]]
The average waiting time is now $(6+0+3)/3=3$ milliseconds.

This difference is substantial and therefore the average waiting time under FCFS is generally not minimal and may vary substantially if the burst time vary greatly.

# Shortest-Job-First Scheduling
A different approach is the shortest-job-first (SJF) algorithm. This algorithm associates with each process the length of the process's next CPU burst. It uses these lengths to schedule the process with the shortest time.

| Process | Burst Time |
|:-------:|:----------:|
|  $P_1$  |     6     |
|  $P_2$  |     8      |
|  $P_3$  |     7      |
|  $P_4$  | 3           |
![[Pasted image 20230911132206.png]]
Average waiting time is $(3+16+9+0)/4=7$ milliseconds.
SJF is optimal for waiting time and it gives minimum average waiting time for a given set of processes. 

Preemptive SJF is Shortest-remaining-time-first.

# Priority Scheduling 
A priority number (integer) is associated with each process and the CPU is allocated to the process with the highest priority (smallest integer = highest priority). SJF is priority scheduling where priority is the inverse of predicted next CPU burst time. A major problem with priority scheduling is indefinite blocking or **starvation** where low priority processes may never execute. A solution to this is **aging** which involves gradually increasing the priority of processes that wait in the system for a long time.

| Process | Burst Time | Priority |
|:-------:|:----------:| -------- |
|  $P_1$  |     10     | 3        |
|  $P_2$  |     1      |       1   |
|  $P_3$  |     2      |      4    |
|  $P_4$  |     1      |    5      |
|  $P_5$  |     5      |    2      |
![[Pasted image 20230911144050.png]]

# Round Robin
Each process gets a small unit of CPU time (time quantum $q$), usually less than 1ms milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue. 

If there are $n$ processes in the ready queue and the time quantum is $q$, then each process gets 1/n of the CPU time in chunks of at most $q$ time units at once. No process waits more than $\cfrac{n-1}{q}$ time units. Timer interrupts every quantum to schedule the next process.

Performance: 
- $q$ large $\to$ FIFO
- $q$ small $\to$ $q$ must be large with respect to context switch, otherwise overhead is too high

| Process | Burst Time |
|:-------:|:----------:|
|  $P_1$  |     24     |
|  $P_2$  |     3      |
|  $P_3$  |     3      |
![[Pasted image 20230911211639.png]]
- Typically, higher average turnaround than SJF, but better response
- $q$ should be large compared to context switch time
- $q$ usually < 1ms, context switch < 10 micro secs

# Multilevel Queue Scheduling 
With both priority and round-robin scheduling, all processes may be placed into a single queue, and the scheduler then selects the process with the highest priority to run. In practice, it is often easier to have separate queues for each distinct priority, and priority scheduling simply schedules the process in the highest priority queue. This is known as **multilevel queue**. 
![[Pasted image 20230911213140.png|centre|200]]
A common division is made between foreground (interactive) and background (batch) processes. These two types have different response-time requirements and different needs. In addition, each queue may have its own scheduling algorithm:
- Foreground: round-robin
- Background: FCFS
Scheduling must be done between the different queues: 
- Fixed priority scheduling (i.e. serve all from foreground then from background). Possibility of starvation
- Time slice - each queue gets a certain amount of CPU time which it can schedule amongst its processes, (i.e. 80% to foreground in RR, 20% to background)
![[Pasted image 20230911213628.png|centre|300]]
# Multilevel Feedback Queue Scheduling
Normally when the multilevel queue scheduling algorithm is used, processes are permanently assigned to a queue when they enter the system. The **multilevel feedback queue** scheduling algorithm in contrast allows a process to move between queues; aging can be implemented this way.

Multilevel-feedback queue scheduler is defined with the following parameters:
- Number of queues
- The scheduling algorithm for each queue
- The method used to determine when to upgrade a process to a higher-priority queue
- The method used to determine when to demote a process to a lower-priority queue
- The method used to determine which queue a process will enter when that process needs service

Example using three queues:
- $Q_0$ - Round Robin with time quantum 8 milliseconds
- $Q_1$ - Round Robin time quantum with 16 milliseconds
- $Q_2$ - FCFS
![[Pasted image 20230911214406.png|centre|300]]
Scheduling:
- A new job enters queue $Q_0$ which is served RR. When it gains CPU, job receives 8 milliseconds. If it does not finish in 8 ms, job is moved to queue $Q_1$ 
- At $Q_1$ job is again served RR and receives 16 additional ms. If it still does not complete, it is preempted and moved into queue $Q_2$ 

