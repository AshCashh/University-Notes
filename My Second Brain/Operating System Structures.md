#cs
A system as large and complex as a modern [[Operating Systems|Operating System]] must be engineered carefully if it is to function properly and be modified easily. A common approach is to partition the task into small components, or modules rather than have a single system. 
![[Pasted image 20230731135526.png|centre|400]]
# Monolithic Structure
The simplest structure for organising an OS is no structure at all. That is, place all of the functionality of the kernel into a single, static binary file that runs in a single address space. This approach is known as a monolithic structure and a common technique for designing OSs

## UNIX
An example of this is the UNIX operating system, which consists of two separable parts: [[System Programs]] and the kernel. 

The kernel is further separated into a series of interfaces and device drivers. 
- Consists of everything below the [[System Calls|System Call]] interface and above the physical [[Hardware]]
- Provides the file system, CPU scheduling, memory management and other OS functions 
![[Pasted image 20230731140804.png|centre|400]]

The Linux OS is based on UNIX and is structured similarly.

# Layered Approach
The monolithic approach is often known as tightly coupled system because changes to one part of the system can have wide-range effects on other parts. Alternatively, we could design a loosely coupled system. Such a system is divided into a number of layers (levels), each built on top of lower layers. The bottom layer (layer 0), is the hardware; the highest (layer N) is the user interface). 
![[Pasted image 20230731142744.png||centre|300]]
All these components together comprise the kernel. 

The main advantage of the layered approach is simplicity of structure and debugging. The layers are selected so that each uses functions (operations) and services of only lower-level layers. The first layer can be debugged without any concern for the rest of the system, because by definition, it uses only the basic hardware to implement its functions.

Layered systems have been successfully used in computer [[Networks]] (such as [[Internet Protocol Suite|TCP/IP]]) and web applications. Nevertheless, relatively few OSs use a pure layered approach as it has challenges of appropriately defining the functionality of each layer. In addition, the overall performance of such systems is poor due to the overhead of requiring a user program to traverse through multiple layers to obtain a [[Operating System Services]]

# Microkernels
As UNIX expanded, the kernel became large and difficult to manage so an OS called Mach (Mac OS X kernel) that modularised the kernel using the micro-kernel approach was created. Another example is QNX, a real-time OS for [[Embedded Systems]]. This method structures the OS by removing all nonessential components from the kernel and implementing them as user-level programs and reside in separate address spaces.
![[Pasted image 20230731143902.png|centre|500]]

Communications takes place between user modules using message passing. For example if the client program wishes to access a file, it must interact with the file server. The client program and service never interact directly.

Benefits of the microkernel approach include:
- Easier to extend and port the OS to new architectures
- More reliable (less code is running in kernel mode)
- More secure

Detriments include:
- Performance overhead of user space to kernel space communication
- Separate address spaces when two services communicate.
- OS may have to switch from one process to the next to exchange messages

# Modules
Perhaps the best current methodology for OS design involves using loadable kernel modules (LKMs). Here, the kernel has a set of core components and can link in additional services via modules, either at boot time or during run time. This type of design is common in modern implementations of UNIX, such as Linux, macOS, Solaris and Windows.
- Uses object-oriented approach
- Each core component is separate and communications over known interfaces
- Each is loadable as needed within the kernel

### Solaris
Solaris is the commercial UNIX-based OS of Sun Microsystems. Originally, Sun's SUNOS OS was based on BSD UNIX. Sun moved to AT&T's System V UNIX as its base in 1991. In 2005, Sun open-sourced most of the Solaris code at the OpenSolaris project. The purchase of Sun by Oracle in 2009 however left the state of this project unclear.

# Hybrid Systems
In practice, very few OSs adopt a single, strictly defined structure. Instead, they combine different structures resulting in hybrid systems that address performance, security and usability issues. For example Linux is monolithic, however it is also modular so that new functionality can be dynamically added to the kernel. Windows is mostly monolithic but it retains some behaviour typical of microkernel systems, including providing support for separate subsystems known as personalities.

