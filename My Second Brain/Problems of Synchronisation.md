#cs #os
In [[Process Synchronisation]], a number of problems like the [[Process Synchronisation#Critical Section Problem|Critical Section Problem]], arise due to concurrent [[Process|Processes]] that may access shared information.

These problems are used for testing nearly every newly proposed synchronisation scheme. In the following solutions, [[Mutex Locks & Semaphores|Semaphores]] will be used for synchronisation as it is the traditional way to present such solutions.
# Bounded-Buffer Problem
The bounded-buffer problem was introduced in [[Inter-Process Communication#IPC in Shared-Memory Systems|Inter-Process Communications]]. Here, we present a general structure of this scheme, such that the producer and consumer processes share the following data structures:
```c
int n; // n buffers, each hold one item
semaphore mutex = 1;
semaphore empty = n; // Count the number empty buffers
semaphore full = 0; // Count the number of full buffers
```
The producer and consumer structure consists of: 

| Producer                             | Consumer |
| :------------------------------------: | :--------: |
| ![[Code Snippets#^ProducerProcess3]] | ![[Code Snippets#^ConsumerProcess3]]         |

# Reader-Writers Problem
Suppose that a database is to be shared among several concurrent processes. 
- **Readers**: Some of these process may only want to read the database, 
- **Writers**: While others may want to update (that is read and write) the database.
The issue arises when multiple readers try to read the database at the same time. 

The problem has several variations of how readers and writers are treated, but all involve priorities. The two problems include:
1. Requires that no reader is kept waiting unless a writer has already obtained permission to use the shared object (i.e. no reader should wait for other readers to finish simply because a writer is waiting). 
2. Requires that once a writer is ready, that writer performs its write as soon as possible (i.e. no new readers may start reading).

A solution to either problem may result in starvation. In the first case, writers may starve; the second, readers may starve. For this reason, other variants have been proposed. 

In the solution to the first problem, the reader processes share the following data structures:
```c
semaphore rw_mutex = 1; // Read/Write mutex (binary)
semaphore mutex = 1; // Ensure mutal exclusion when count is updated
int read_count = 0; // Count num processes currently reading
```
Below is the structure of the reader and writer process:

| Writer Process                    | Reader Process |
| :---------------------------------: | :--------------: |
| ![[Code Snippets#^WriterProcess]] | ![[Code Snippets#^ReaderProcess]]               |

Note that, if a writer is in the critical section and n readers are waiting, then one reader is queued on `rw_mutex`, and $n − 1$ readers are queued on mutex. Also observe that, when a writer executes `signal(rw_mutex)`, we may resume the execution of either the waiting readers or a single waiting writer. The selection is made by the scheduler.

The readers-writers problem and its solutions have be generalised to provide reader-writer locks on some systems.

# Dining-Philosopher's Problem 
Consider five philosophers who spend their lives thinking and eating. The philosophers share a circular table surrounded by five chairs:
![[Pasted image 20230821133957.png|centre|300]]
In the centre of the table is a bowl of rice and the table is laid with five single chopsticks. When a philosopher thinks, they do not interact with the other 4 philosophers. From time to time, a philosopher gets hungry and tries to pick up the two chopsticks that are closest to them (they are in between themselves and the left and right neighbours). A philosopher may pick up only one chopstick at a time.

In this problem, one solution is to represent each chopstick with a semaphore. A philosopher tries to grab a chopstick by executing `wait()` on that semaphore. They release the chopstick by executing the `signal()` operation. Thus the shared data is:
```c
semaphore chopstick[5]; // Where all elements are initilised to 1
```
And one incorrect solution consists of:
```c
while (true){
	wait(chopstick[i]);
	wait(chopstick[i + 1 % 5]);
	...
	// Eat for a while
	...
	signal(chopstick[i]);
	signal(chopstick[i + 1 % 5])
	...
	// Think for a while
	...
}
```
Although this solution guarantees that no two neighbours are eating simultaneously, it will fail and could create a deadlock. Suppose that all five philosophers become hungry at the same time and each grabs their left chopstick. All the elements of `chopstick` will now be equal to 0. 

