The processes in most systems can execute concurrently, and they may be created and deleted dynamically. Thus, these systems must provide a mechanism for process creation and termination.

# Process Creation
During the course of execution, a process may create several new processes. The creation of a process is called a parent process, and the new processes are called the children of that process, forming a tree of processes. 

Most OSs identify processes according to a unique process identifier (pid), which provides a unique integer for each process and is used as an index to access various attributes of a process within the kernel.

When a child is create, two possibilities for execution exist: 
- The parent continues to execute concurrently with its children
- The parent waits until some or all of its children have terminated.
There are also address-space possibilities (resource sharing):
- Parent and children share all resources
- Children share subset of parent's resources
- Parent and child share no resources (default on Linux)

A new process is created by the `fork()` [[System Calls|System Call]]. The new process consists of a copy of the address space of the original process. The return code for the `fork()` is zero for the new child process, whereas the nonzero process identifier of the child is returned to the parent. 

Once forked, it's typical for `exec()` to be called on one of the two processes. The `exec()` system call loads a binary file into memory (destroying the memory image of the program containing the exec() system call) and starts its execution.

For example, this code forks a new process and using `execlp()`, a version of the `exec()` system call, overlays the process address space with the UNIX command `/bin/ls` (used to get a directory listing)
```c
#include <sys/types.h>
#include <sys/wait.h>
#include <stdio.h>
#include <unistd.h>
int main() 
{ 
pid_t pid; 

	// fork a child process  
	pid = fork(); 
	if (pid < 0) { // error occurred  
		fprintf(stderr, "Fork Failed"); 
		return 1; 
	} 
	else if (pid == 0) { /* child process */ 
		execlp("/bin/ls","ls",NULL); 
	} 
	else { // parent process 
		wait(NULL); // waits for the child to terminate
		printf("Child Complete"); 
	} 
	return 0; 
}
```
![[Pasted image 20230804224847.png|500]]

# Process Termination
A process terminates when it finishes executing its final statement and asks the OS to delete it by using the `exit()` system call. At that point, the process may return a status value (typically an integer) to its waiting parent process (via the `wait()` system call).

A parent may terminate the execution of one of its children for a variety of reasons, such as:
- The child has exceeded its usage of some of the resources that it has been allocated `abort()`
- The task assigned to the child is no longer required 
- The parent is exiting and the OS does not allow a child to continue if its parent terminates

A parent process may wait for the termination of a child process by using the `wait()` system call. The `wait()` system call is passed as a parameter that allows the parent to obtain the exit status of the child. This system call also returns the process identifier of the terminated child so the parent can tell which of its children terminated.
```c
pid_t pid;
int status;

pid = wait(&status);
printf("Child exited with %d\n", pid);
```
When a process terminates, its resources are deallocated by the OS. However its entry in the process table must remain there until the parent calls `wait()`, because the process table contains the process's exit status.

If a child process is terminated but the parent has not called `wait()`, the process is known as a zombie process. If a parent is terminated before calling `wait()`, the process is known as an orphan.