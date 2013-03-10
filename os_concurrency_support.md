## OS Support for Concurrent Programming

### OS Multiprocessing Mechanisms
Multiprocessing mechanisms include the features provided by the OS for creating and managing the execution of multiple processes

  * **Process Lifetime Operations**
    * create a new process address space for programs to run
    * e.g. `fork()` and `exec()` on POSIX and `CreateProcess()` on Windows
    * The parent process can set command line arguments, environmental variable & working directories for the child process
    * The child process can terminate _voluntarily_ by reaching the end of its execution of be _involuntarily_ killed via signals (in POSIX) or `TerminateProcess()` (in Windows)
  * **Process Synchronization Options**
    * provided by the OS to retain the identity and exit status of a process and report it to the parent
    * POSIX `wait()` and `waitpid()`
    * Windows `WaitForSingleObject()` and `WaitForMultipleObjects()`
  * **Process Property Operations** &mdash; used to get/set process properties, e.g.
      * default file access permissions
      * user identification
      * resource limits
      * scheduling
      * priority
      * current working directory

### OS Multithreading Mechanisms
Multithreading mechanisms are provided by the OS to handle thread lifetime management, synchronization, properties, and thread-specific storage

  * **Thread Lifetime Operations** &mdash; include operations to:
    * Create threads, e.g. `pthread_create()` (PThreads) & `CreateThread()` (Windows)
    * Terminate threads
      * _Voluntarily_ &mdash; by reaching the end point of the thread entry function or calling `pthread_exit()` (PThreads) or `ExitThread()` (Windows)
      * _Involuntarily_ &mdash; by being killed via signal or an asynchronous thread cancelation operations, such as `pthread_cancel()` (PThreads) and `TerminateThread()` (Windows)
  * **Thread Synchronization Operations** &mdash; enable created threads to be:
    * _Detached_ &mdash; where the OS reclaims storage used for the thread's state and exit status after it has exited
    * _Joinable_ &mdash; where the OS retains identity and exit status of a terminating thread so other threads can synchronize with it
    * Operating systems differ considerably with regard to their native support for threads
  * **Thread Property Operations** &mdash; includes operations to set and get thread properties, such as priority and scheduling class
  * **Thread-Specific Storage** &mdash; is similar to global data except that the data is only "global" in the scope of the executing thread

### Concurrent Programming Summary

  * Operating Systems provide concurrency mechanisms that manage multiple processes on an end system and manage multiple threads that run concurrently within a process
  * Developing concurrent and networking apps using native OS concurrency mechanism can cause portability, reliability, and sustainment problems
  * A lot of "accidental" complexities
  * When used in conjunction with the appropriate _patterns_ and _frameworks_, concurrency helps to improve performance and simplify program structure

## OS Synchronization Mechanisms
Synchronization mechanisms allow processes and threads to coordinate their execution order and the order in which they access shared resources

  * **Mutexes** 
    * Serialize execution of multiple threads by defining a _critical section_ that can be executed by one thread at a time
    * _Nonrecursive mutex_
      * Will deadlock or fail if thread owning mutex tries to reacquire it without releasing it
      * Thread owning mutex must release it
    * _Recursive mutex_
      * Will allow thread owning mutex to reacquire it without deadlocking
      * Owner thread must release it same # of times it acquired it
  * **Reader/Writer Locks**
    * Allows access to a shared resource by either multiple threads simultaneously having read-only access or only one thread at a time having write access
  * **Semaphores**
    * A non-negative integer that can be incremented and decremented atomically
    * A thread/process blocks when it tires to decrement a semaphore whose value is 0
    * A blocked thread/process makes progress when another thread/process increments the semaphore
    * Semaphores are often implemented via sleep locks, which trigger a context switch
  * **Condition Variables**
    * Allows a thread to coordinate and schedule its own processing
    * A thread can wait on complex expressions to attain a desired state
    * Often used as building-blocks for patterns, such as _Active Object_ and _Monitor Object_

### Synchronization Summary

  * Synchronization mechanism performance depends on OS implementation, hardware, and use cases
  * Some issues to keep in mind:
    * **Condition variables** and **semaphores** generally have a higher overhead than **mutexes**, but they are also more expressive
    * **Mutexes** vs. **Readers/Writer Locks**
      * Mutexes generally have lower overhead than readers/writer locks
      * But readers/writer locks may enable more parallelism on multi-core processors
    * **_Nonrecursive_ mutexes** are more efficient than **_recursive_ mutexes**, but they are also more _error-prone_
  * Not all operating systems support all these synchronization mechanisms, so it may be necessary to emulate some mechanisms in terms of others to ensure portability




