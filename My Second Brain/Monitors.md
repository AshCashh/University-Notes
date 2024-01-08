#cs #os
Although [[Mutex Locks & Semaphores|Semaphores]] provide a convenient and effective mechanism for [[Process Synchronisation]], using them incorrectly can result in timing errors that are difficult to detect. One strategy for dealing with such errors is to incorporate simple synchronisation tools as high-level abstraction that provides a convenient and effective mechanism for process synchronisation.

An abstract data type or ADT - encapsulates data with a set of functions to operate on that data that are independent of any specific implementation of the ADT and only accessible by code within the function.

The monitor construct ensures that only one process at a time is active within the monitor. Consequently, the programmer does not need to code this synchronisation constraint explicitly. In some instances, however, we need to define additional synchronisation mechanisms. These mechanisms are provided by the `condition` construct. A programmer who needs to write a tailor-made synchronisation scheme can define one or more variables of type condition. The only operations that can be invoked on a condition variable are `wait()` and `signal()`.

The `wait()` means that the process invoking this operation is suspended until another process invokes, whereas the `signal()` operation resumes exactly one suspended process. If no process is suspended, then the `signal()` operation has no effect. Contrast this operation with the `signal()` operation associated with semaphores, which always affects the state of the semaphore.

Now suppose that when the `x.signal()` operation is invoked by a process $P$, there exists a suspended process $Q$ associated with condition `x`. Clearly, if the suspended process $Q$ is allowed to resume its execution, the signalling process $P$ must wait. Otherwise, both $P$ and $Q$ would be active simultaneously within the monitor. Two possibilities exist:
1. **Signal and wait**: $P$ either waits until $Q$ leaves the monitor or waits for another condition.
2. **Signal and continue**: $Q$ either waits until $P$ leaves the monitor or waits for another condition.

