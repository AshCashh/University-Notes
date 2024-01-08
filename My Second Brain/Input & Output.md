---
alias: I/O
---
#cs #os
In [[Computer Science]], input/output (I/O) is the communication between an information processing system (a compiler) and the outside world, possibly a human or another IPS.

## I/O Structure
There are two ways I/O is structured:
1. After I/O starts, control returns to user program only upon I/O completion.
	- Wait instruction idles the CPU until the next [[Interrupts|Interrupt]]
	- Wait loop (contention for memory access)
	- At most one I/O request is outstanding at a time, no simultaneous I/O processing
2. After I/O starts, control returns to user program without waiting for I/O completion
	- System call - request to the [[Operating Systems]] to allow user to wait for I/O completion
	- Device - status table contains entry for each I/O device indicating its type, address and state
	- OS indexes into I/O device table to determine device status and to modify table entry to include interrupt.

