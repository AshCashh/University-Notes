#os
# Pthreads
Pthreads refers to the POSIX standard (IEEE 1003.1c) API for thread creation and synchronisation, which may be provided as either a user-level or kernel-level library. This is a specification for thread behaviour not a implementation. It is commonly implemented in UNIX type systems, including Linux and macOS.
```c
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>

int sum; /* this data is shared by the thread(s) */ 
void *runner(void *param); /* threads call this pointer function */ 

int main(int argc, char *argv[]) 
{ 
	pthread_t tid; /* the thread identifier */ 
	pthread_attr_t attr; /* set of thread attributes */ 
	
	/* set the default attributes of the thread */ 
	pthread_attr_init(&attr); 
	/* create the thread */ 
	pthread_create(&tid, &attr, runner, argv[1]); 
	/* wait for the thread to exit */ 
	pthread_join(tid,NULL); 
	
	printf("sum = %d∖n",sum); 
} 
/* The thread will execute in this function */ 
void *runner(void *param) 
{ 
	int i, upper = atoi(param); 
	sum = 0; 
	for (i = 1; i <= upper; i++) {
		sum += i; 
	}
	pthread_exit(0); // not entirely necessary
}
```
Above demonstrates the basic Pthreads API for constructing a multithreaded program that calculates the summation of a non-negative integer in a separate thread.

# [[Mutex Locks & Semaphores|Mutex Locks]]
```c
pthread_mutex_t lock;
pthread_mutex_init(&lock, NULL); // Initilisation
```
Locking:
```c
int globalVar = 0;
if (pthread_mutex_lock(&lock)){ // Will wait if the mutex is currently aquired 
	perror("pthread_mutex_lock"); // Error if trying to lock a mutex thats already locked or locking a different mutex
} 

globalVar++ // Protected - wont be rearranged in memory

if (pthread_mutex_unlock(&lock)){
	perror("pthread_mutex_unlock"); // Error if trying to unlock a mutex thats already unlocked
} 
```

# [[Threads#Thread Scheduling|Thread Scheduling]]
API allows specifying either PCS or SCS during thread creation:
```c
PTHREAD_SCOPE_PROCESS // Schedules threads using PCS scheduling NONLINUX
PTHREAD_SCOPE_SYSTEM // Schedules threads using SCS scheduling. LINUX
```
This specification of either a kernel or user thread is done during thread creation.
Below is an example of implementing the Pthread scheduling API
```c
#include <pthread.h>
#include <stdio.h>
#define NUM_ThREAD 5

int main(int argc, char *argc[]){
	int i, scope;
	pthread_t tid[NUM_THREAD];
	pthread_attr_t attr;

	// Get the default attributes
	pthread_attr_init(&attr);

	// First inquire on the current scope
	if (pthread_attr_getscope(&attr, &scope) != 0){
		fprintf(stderr, "Unable to get scheduling scope");
	}
	else{
		if (scope == PTHREAD_SCOPE_PROCESS){
			printf("PTHREAD_SCOPE_PROCESS");
		}
		else if (scope == PTHREAD_SCOPE_SYSTEM){
			printf("PTHREAD_SCOPE_SYSTEM"); // Will be system as linux
		}
		else{
			fprint(stderr, "Illegal scope value");
		}
	}
	// Set the scheduling algorithm to PCS or SCS
	pthread_attr_setscope(&attr, PTHREAD_SCOPE_SYSTEM);

	// Create the threads
	for (i = 0; i < NUM_THREADS; i++){
		pthread_joint(tid[i], NULL);
	}
}
// Each thread will begin control in this function
void *runner(void *param){
	// Do some work
	pthread_exit(0);
}