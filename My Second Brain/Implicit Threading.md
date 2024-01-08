#cs #cs
One way to address the difficulties and better support the design of [[Multithreading Models|Multithreading]] applications is to transfer the creation and management of [[Threads|Threading]] from application developers to compilers and run-time libraries. This strategy, termed implicit threading, is an increasingly popular trends.

# Thread Pools
The idea behind a thread pool is to create a number of threads at start-up and place them into a pool, where they sit and wait for work. 

When a server receives a request, rather than creating a thread, it submits the request to the pool and resumes waiting for additional requests. If the pool contains no available threads, the task is queued until one becomes free.

Thread pools offer the following advantages:
- Usually slightly faster to service a request with an existing thread than create a new one.
- Allows the number of threads in the application(s) to be bound to the size of the pool.
- Separating the task to be performed from the mechanics of creating the task allows different strategies for running the task. I.e. could be scheduled to run periodically.

# OpenMP
OpenMP is a set of compiler directives as well as an API for programs written in C that provides support for parallel programming in shared-memory environments. OpenMP identifies parallel regions as blocks of code that may run in parallel. Application developers insert compiler directives into their code at parallel regions and these directives instruct the OpenMP run-time library to execute the region in parallel. 

The following C program illustrates a compiler directive above the parallel region containing the `printf()` statement:
```c
#include <omp.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
	// Sequential code

	#pragma omp parallel
	{
		printf("I am a parallel region");
	}

	// Sequential code
	return 0;
}
```
The `#pragma omp parallel` will create as many threads as there are cores. The following example demonstrates how to run a for loop in parallel:
```c
#pragma omp parallel for
{
	for(int i = 0; i < N; i++){
		c[i] = a[i] + b[i];
	}
}
```
