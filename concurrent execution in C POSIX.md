 

POSIX stands for portable operation system interface. It allows concurrent programming. There are three mechanisms for concurrent activities:

1.  Traditional process level Unix-fork mechanism: This causes a copy of the entire process to be created and executed
    
2.  The second is the spawn system call, which is equivalent in function to a combined fork and exec.
    

POSIX also allows for each process to contain several threads that share the same memory and address space. All threads have attributes. These attributes give more information about the thread, like stack-size and any overflow buffer. To manipulate the attributes it is necessary to define an attribute object. Every thread has an associated identifier. A thread becomes eligible for execution as soon as it is created. A thread can terminate by returning from its start_routine, by calling pthread_exit or by receiving a signal sent to it. One thread can wait for another to terminate by the pthread_join. The activity of cleaning up after a thread’s execution and reclaiming its storage is termed ‘detaching’. There are two ways to do this the first is by calling the pthread_join function and waiting for the thread to finish and the second is to set the detach attribute of the thread. If the detach attribute is said the storage space may be reclaimed as soon as the thread terminates.