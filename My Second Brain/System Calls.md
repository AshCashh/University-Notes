#cs
System calls provide an interface to the services made available by an [[Operating Systems]]. These calls are generally available as functions written in C and C++.

Example of system calls to copy contents of one file to another file:
![[Pasted image 20230731121559.png|centre|400]]

## Application Programming Interface
System calls are mostly accessed by programs via a high-level [[Application Programming Interface]] (API) rather than direct system call use. The API specifies a set of functions that are available to an application programmer, including the parameters that are pass and the return values. Three of the most common APIs are Win32 API for Windows, POSIX API for POSIX-based systems (including virtually all versions of UNIX, Linux and Mac OS X) and Java API for the Java virtual machine (JVM).

![[Pasted image 20230731122001.png|400]]

## System Call Implementation
Typically, a number is associated with each system call, and the system-call interface maintains a table indexed according to these numbers. The system-call interface then invokes the intended system call in the OS kernel and returns the status of the system call.

The caller needs to know nothing about how the system call is implemented or what it does during execution.
- Just needs to obey API and understand what OS will do as a result call
- Most details of OS interface hidden from programmer by API. Managed by run-time support library (set of functions built into libraries included with compiler)

### Parameter Passing
Often, more information is required than simply the identity of the desired system call. The exact type and amount of information vary according to the particular OS and call. Three general methods are used to pass parameters to the OS:
1. Simplest: Pass the parameters in registers, if theres more parameters then registers then:
2. Parameters stored in a block or table, into memory and the address of the block is passed as a parameter in a register.
	- Approach taken by Linux and Solaris
3. Parameters placed, or pushed on the stack by the program and popped off by the OS
Note that block and stack methods do not limit the number or length of parameters being passed.
![[Pasted image 20230731124203.png|400]]

## System Call Types
System calls can be grouped roughly into six major categories: 
1. **Process control**: end, abort, load, execute. Create process/terminate. Get/set process attributes. Wait for time/event/signal event. Allocate and free memory. Dump memory if error. Debugger for determining bugs, single step execution. Locks for managing access to shared data between processes
2. **File Managements:** Create/delete/open/close file. Read/write/reposition. Get/set file attributes
3. **Device Management:** Request/release device. Read/write/reposition. Get/set device attributes. Logically attach/detach devices
4. **Information maintenance:** Get/set time or date. Get/set System data. Get/set process, file or device attributes
5. **Communications**: Create/delete communication connection. Send/receive messages if message passing model to host name or process name. Shared-memory model create and gain access to memory regions. Transfer status information. Attach and delete remote devices.
6. **Protection**: Get/set file permissions. Control access to resources. Allow/deny user access
![[Pasted image 20230731125242.png|400]]

### Example: FreeBSD
Unix variant, multitasking, user login -> invoke user's choice of shell. 
Shell executes `fork()` system call to create process:
- Executes `exec()` to load program into process
- Shell waits for process to terminate or continues with user commands.
Process exists with code of 0 - no error or > 0 - error code
![[Pasted image 20230731130252.png|300]]

### Example: Standard C Library
C program invoking `printf()` library call, which calls `write()` system call.
![[Pasted image 20230731133634.png|400]]


