**Reliability is a key requirement of real-time and embedded systems. Discuss this, and indicate how the different programming languages that we have discussed and the operating systems. try to offer answers to possible problems. Be as complete as possible and certainly do not limit your answers to Chapters 2 and 3.**

---

knowledge used: 
- [[Chapter 02 Reliability and Fault Tolerance]], 
- [[Chapter 03 Exceptions and Exception Handling]], 
- [[Chapter 13 Tolerating timing faults]], 
- [[Chapter 07 Atomic actions, concurrent tasks and reliability]], 
- [[Chapter 13 Tolerating timing faults]]. 

---

- fault prevention
	- [[programming language comparison in fault prevention]]
	- [[deadlock]] prevention

- fault tolerance (based on redundancy)
	- static redundancy: [[N-version programming]]
	- dynamic redundancy
		- Error detection
			- Detection by the environment
			- Detection by the application
		- Damage confinement and assessment
			- modular decomposition (static) (limit the error propagation)
			- atomic actions (dynamic)
			- protection of concurrent use of resources (limit access to specific functions)
			- limit access to concurrent memory by [[semaphore]], [[monitor in C POSIX]], etc. 
		- Error recovery: [[forward recovery]] and [[backward recovery]]
		- treatment of error

- exception handling: dynamic [[forward recovery]]
	- throwing exception is only not supported in C
	- Ada, Java, and C++ use the [[termination model]]

| Ada                                       | Java                                              | C++                     |
| ----------------------------------------- | ------------------------------------------------- | ----------------------- |
| every block can have an exception handler | block should be guarded                           | block should be guarded |
|                                           | `try` block                                       |                         |
| provide procedure `Exception_Information` | add informatoin to exceptions (defined as object) |                         |
