An [[Operating Systems|Operating System]] provides an environment for the execution of programs and services to programs and users.
![[Pasted image 20230730141708.png]]
- **User Interface (UI)**: Almost all OSs have a user interface. Most commonly a graphical user interface (GUI) is used although command-line interface (CLI) or Batch is also seen.
- **Program Execution**: The system must be able to load a program into memory and to run that program, end execution, either normally or abnormally (indicating error)
- **[[Input & Output|I/O]] Operations:** A running program may require I/O, which may involve a file or an I/O device.
- **File-System Manipulation**: Programs need to read and write files and directories, create and delete them, search, list file information and permission management.
- **Communications:** Processes may exchange information, on the same computer or between computers via a [[Networks|Network]]
- **Error Detection:** OS needs to be constantly aware of possible errors
	- Many occur in the CPU and memory hardware, in I/O devices in user program
	- For each type of error, OS should take the appropriate action to ensure correct and consistent computing
	- Debugging facilities can greatly enhance the user's and programmer's abilities to efficiently use the system
- **Resource Allocation:** When multiple users or multiple jobs running concurrently, resources must be allocated for each of them.
	- Many types of resources - some (such as CPU cycles, main memory, and file storage) may have special allocation code, others (such as I/O devices) may have general request and release code
- **Accounting:** To keep track of which users use how much and what kinds of computing resources
- **Protection and Security:** The owners of information stored in a multiuser or networked computer system may want to control use of that information, concurrent processes should not interfere with one another.
	- Protection: Involves ensuring that all access to system resources is controlled
	- Security: Of a system from outsiders requires user authentication, extends to defending external I/O devices from invalid access attempts
	If a system is to be protected and secure, precautions must be instituted throughout it. A chain is only as strong as its weakest link.

## User Operating System Interface
There are several ways for users to interface with the OS. One of which provides a command-line interface (CLI), or command interpreter, that allows users to directly enter commands to be performed by the OS.

### Command Interpreters
Most OSs treat the command interpreter as a special program that is running when a process is initiated. On systems with multiple command interpreters to choose from, the interpreters are known as shells (e.g. C shell, Bourne-Again shell, Korn shell). As mentioned they primarily fetch a command from a user and execute it.

### Graphical User Interface (GUI)
Rather than implementing commands via a CLI, users employ a mouse-based window and menu system characterised by a desktop metaphor. Icons represent files, programs, actions, etc. Various mouse buttons over objects in the interface cause various actions (provide information, options, execute function, etc).

Many systems include a CLI and GUI, for example:
- Microsoft Windows is GUI with CLI "command" shell
- Apple Mac OS X is "Aqua" GUI interface with UNIX kernel underneath and shells available
- Unix and Linux have CLI with optional GUI interfaces (CDE, KDE, GNOME)

### Touchscreen Interfaces
Users interact by making gestures on the touch screen with virtual keyboards for text entry and requires physical interaction. 
