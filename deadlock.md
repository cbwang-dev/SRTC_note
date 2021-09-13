- deadlock and livelock
	- deadlock -> [[starvation]]
		- process A is allocated the printer and waits for the tape
		- process B is allocated the tape and waits for the printer
	- livelock -> [[liveness]]
		- process A is allocated the printer and polls actively to see if the tape is free
		- process B is allocated the tape and polls actively to see if the printer is free
- **4 necessary conditions for deadlock**
	- [[mutual exclusion]] of used resources
	- hold and wait: processes allocated to resources wait for other resources
	- no [[pre-emption]] of resources (one can not take away resources allocated to others)
	- circular wait (closed chain of processes that wait on resources allocated to the following process)
- 3 methods for treating deadlock
	- prevention: make sure that one of the 4 conditions does not occur
		- [[mutual exclusion]]: difficult, some resources are simple exclusive
		- hold and wait: one can allocate all resources at the same time (all or nothing), inefficient
		- no [[pre-emption]]: de-allocate (difficult to recover the state of process)
		- **circular wait**: put strict order on allocating resources, resources can only be requested in that order
	- avoidance: dynamic process
		- record dynamically during run time
			- resources allocated 
			- resources requested 
			- total need of resources 
		- cons: 
			- difficult, complicated algorithm to solve, not always feasible
				- maximum needs of an application (`max needed` in the following table) are often not known by system/application
			- cost for the system is high
		- example: system with 12 tape units (table 1 below)
			- example 1: 3 tapes left, enough to let `P1` complete; Then 5 tapes left, enough to let `P0` complete; Then `P2` can complete. 
			- example 2: 2 tapes left, enough to let `P1` complete; Then 4 tapes left, not sufficient for either `P0` or `P2` complete, resulting in a deadlock. 
		- example: deadlock while using semaphore (table 2 below)
	- detection and recovery (breaking deadlock)
		- detection based on following knowledge
			- what is already allocated
			- which resources are requested but are not free
			- build a graph, if there is a cycle, then there is a deadlock
		- breaking a detected deadlock
			- sharing a resource
			- stop a process early
			- take away a resource

| process | allocated 1 | max needed 1 | allocated 2 | max needed 2 |
| ------- | ----------- | ------------ | ----------- | ------------ |
| P0      | 5           | 10           | 5           | 10           |
| P1      | 2           | 4            | 2           | 4            |
| P2      | 2           | 9            | 3           | 9            | 

| P1                                | P2                                |
| --------------------------------- | --------------------------------- |
| `lock(s)`                         | ...                               |
| status: `s` change from 1 to 0    | ...                               |
| ...                               | `lock(r)`                         |
| ...                               | status: `r` change from 1 to 0    |
| `lock(r)`                         | ...                               |
| status: `r` is already 0, so wait | ...                               |
| ...                               | `lock(s)`                         |
| ...                               | status: `s` is already 0, so wait | 
| deadlock                          | deadlock                          |
