# Multi-thread

## Difference between a thread and a process

Processes and threads are related to each other but are fundamentally different.

A process can be thought of as an instance of a program in execution. Each process is an independent entity to which system resources \(CPU time, memory, etc.\) are allocated and each process is executed in a separate address space. One process cannot access the variables and data structures of another process. If you wish to access another process’ resources, inter-process communications have to be used such as pipes, files, sockets etc.

A thread uses the same stack space of a process. A process can have multiple threads. A key difference between processes and threads is that multiple threads share parts of their state. Typically, one allows multiple threads to read and write the same memory \(no processes can directly access the memory of another process\). However, each thread still has its own registers and its own stack, but other threads can read and write the stack memory.

A thread is a particular execution path of a process; when one thread modifies a process resource, the change is immediately visible to sibling threads.

## Volatile 

If a variable is declared with the _volatile_ keyword then it is guaranteed that any thread that reads the field will see the most recently written value. The _volatile_ keyword will not perform any mutual exclusive lock on the variable.

As of Java 5 write access to a _volatile_ variable will also update non-volatile variables which were modified by the same thread. This can also be used to update values within a reference variable, e.g. for a _volatile_ variable person. In this case you must use a temporary variable person and use the setter to initialize the variable and then assign the temporary variable to the final variable. This will then make the address changes of this variable and the values visible to other threads.



