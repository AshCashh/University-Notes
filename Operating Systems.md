#cs
An operating system (OS) is system software that manages computer [[Hardware]] and [[Software]] resources and provides common services for computer programs.

For hardware functions such as input and output and memory allocation, the operating system acts as an intermediary between programs and the computer hardware, although the application code is usually executed directly by the hardware and frequently makes system calls to an OS function or is interrupted by it. 

# What OS's Do
A computer system can be divided roughly into four components: the [[Hardware]], operating system, the application programs and the user. The hardware - the CPU, the memory and the I/O devices provide basic computing resources for the system. The application programs - such as word processors, spreadsheets, compilers and web browsers define the ways in which these resources are used to solve users' computing problems. The OS controls the hardware and coordinates its use among the various application programs for the various users.

Users want convenience, ease of use and don't care about resource utilisation. However shared computers such as mainframe or minicomputer must keep all users happy. Users of dedicated systems such as workstations have dedicated resources but frequently use shared resources from servers. Handheld computers (phones, tablets, etc) are resource poor, optimised for usability and battery life. Some computers have little or no user interface, such as [[Embedded Systems|Embedded Computers]] in devices and automobiles.

## Computer Startup
Bootstrap program is loaded at power-up or reboot. Typically stored in ROM or EPROM, generally known as firmware. It initialises all aspects of a system and loads operating system kernel and starts execution.


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