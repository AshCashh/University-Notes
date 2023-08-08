#cs
An operating system (OS) is system software that manages computer [[Hardware]] and [[Software]] resources and provides common services for computer programs.

For hardware functions such as input and output and memory allocation, the operating system acts as an intermediary between programs and the computer hardware, although the application code is usually executed directly by the hardware and frequently makes system calls to an OS function or is interrupted by it. 

# Types of Operating Systems
## Single-Tasking and Multi-Tasking
A single-tasking system can only run one program at a time, while a multi-tasking operating system allows more than one program to be running concurrently. This is achieved by time-sharing, where the available processor time is divided between multiple processes. These processes are each interrupted repeatedly in time slices by a task-scheduling subsystem of the operating system. Multi-tasking may be characterised in preemptive and cooperative types.

## Single-user and multi-user
Single-user operating systems have no facilities to distinguish users but may allow multiple programs to run in tandem. A multi-user operating system extends the basic concept of multi-tasing with facilities that identify processes and resources, such as disk space, belonging to multiple users and the system permits multiple users to interact with the system at the same time.

## Distributed
A distributed operating system manages a group of distinct, networked computers and makes them appear to be a single computer, as all [[Computation|Computations]] are distributed.

## Embedded
[[Embedded Systems]] are designed to be used in embedded computer systems. They are designed to operate on small machines with less autonomy (e.g. PDAs). They are very compact and extremely efficient by design and are able to operate with a limited amount of resources. Windows CE and Minix 3 and some examples.

## Real-Time
A real-time operating system is an operating system that guarantees to process events or data by a specific moment in time. A real-time operating system may be single or multi-tasking, but when multitasking it uses specialised scheduling algorithms so that a deterministic nature of behaviour is achieved. 


# Week 1
[[Computer System]]
[[Interrupts]]
[[Input & Output|I/O]]

# Week 2
[[Operating System Structures]]:
- [[Operating System Structures#Monolithic Structure|Monolithic Structure]]
- [[Operating System Structures#Layered Approach|Layered Approach]]
- [[Operating System Structures#Microkernels|Microkernels]]
- [[Operating System Structures#Hybrid Systems|Hybrid Systems]]
[[Operating System Services]]
[[System Calls]]
[[System Programs]]
# Week 3
[[Process]]:
- [[Process#Process Control Block|PCBs]]
[[Process Scheduling]]:
- [[Process Scheduling#Schedulers|Schedulers]]
- [[Process Scheduling#Context Switch|Context Switch]]
[[Operations on Processes]]:
- [[Operations on Processes#Process Creation|Process Creation]]
- [[Operations on Processes#Process Termination|Process Termination]]
[[Inter-Process Communication]]
