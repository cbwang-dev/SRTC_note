When a number of processes or threads share variables
-  the code snippets where those variables are manipulated = critical section
-  only one process/thread may enter a critical section at the same time
-  the critical sections must be protected

```
code without access to shared variables
	lock(semaphore)   -----|
critical section           |- protocol
	unlock(semaphore) -----|
code without access to shared variables
```

 

critical sections have multiple sub problems: 
- [[mutual exclusion]] (Correctness)
	- a maximum of one process/thread is allowed in its critical section 
- progress(Liveness)
	- only processes/threads that are not in their critical section are allowed to participate
	- decision may not be postponed indefinitely 
- upper limit on waiting time (Fairness)
	- upper limit on number of times being bypassed