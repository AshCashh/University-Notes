---
alias: Processes
---
#cs #os
An [[Operating Systems]] executes a variety of programs, either a Batch system (jobs) or a Time-shared system (user program or task). A process is a program in execution and must progress in sequential fashion. A process consists of multiple parts:
- **Text Section**, containing the executable code
- The current activity, i.e. the **Program Counter** and the contents of the processors register
- The **Stack Section**, consisting of temporary data such as function parameters, return addresses and local variables
- The **Data Section**, containing global variables
- The **Heap Section**, containing memory that is dynamically allocated during run time
![[Pasted image 20230803204240.png|centre]]
We emphasise that a program by itself is not a process. A program is a passive entity stored on disk (executable file). In contrast a process is an active entity. A program becomes a process when an executable file is loaded into memory. Multiple processes may be associated with the same program, like when several users are executing the same program.

## Process State
As a process executes, it changes state. The state of a process is defined in part by the current activity of that process. A process may be in one of the following states:
- **New**: The process is being created
- **Running**: [[Instructions]] are being executed
- **Waiting**: The process is waiting for some event to occur (such as an I/O completion or reception of a signal)
- **Ready**: The process is waiting to be assigned to a processor
- **Terminated**: The process has finished execution
![[Pasted image 20230803204651.png|centre|500]]

## Process Control Block
Each process is represented in the OS by a process control block (PCB) - also called a task control block. A PCB contains many pieces of information associated with a specific process:
- Process state: The state may be new, ready, running, waiting, halted, etc
- Program counter: The counter indicates the address of the next instruction to be executed
- CPU registers: Contents of all process-centric registers
- CPU scheduling information: Includes process priority, scheduling queue pointers
- Memory-management information: Memory allocated to the process
- Accounting information: CPU used, clock time elapsed since start, time limits
- I/O status information: I/O devices allocated to process, list of open files

![[Pasted image 20230803223831.png|centre|300]]
In brief, the PCB simply serves as the repository for all the data needed to start, or restart, a process along with some accounting data.
## [[Threads]]
The process model discussed so far has implied that a process is a program that performs a single thread of execution. However, most modern OS have extended the process concept to allow a process to have multiple threads of execution and thus to perform more than one task at a time. This feature is especially beneficial on multicore systems, where multiple threads can run in parallel. A multithreaded word processor could for example, assign one thread to manage user input while another runs the spell checker. On systems that support threads, the PCB is expanded to include information for each thread. 
### Process Representation in Linux
![[Pasted image 20230803230033.png|400]]





