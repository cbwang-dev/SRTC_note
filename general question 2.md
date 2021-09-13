**Compare and contrast the use of X1 and the use of X2 for programming both a real-time application and an application for an embedded device. Be detailed and specific, and be as complete as possible. X1 and X2 can be one of the following: Ada, C/POSIX, RTSJ**

---

1. Comparisons between [[RT systems]] and [[embedded systems]]. Then, run into [[characteristics of RT systems]]. 
2. We will discuss the following 4 **bold** characteristics out of 7 in [[characteristics of RT systems]]. 
	1. **dealing with  'time', real time control possibilities** Ch9-Ch12
	2. **different software components: simultaneously active** Ch4-6, Ch7-8
	3. **interactions with hardware interface** Ch14
	4. requirement for efficient implementation
	5. manipulation of real numbers (for you to read)
	6. large and complex
	7. **extremely reliable and secure** Ch2-3, Ch7, Ch13

---

### extremely reliable and secure -> reliability
- fault prevention
	- [[programming language comparison in fault prevention]]
- fault tolerance (achieved by redundancy)
	- static redundancy
		- [[N-version programming]]. In this, different languages can be used in parallel to implement a single function (one version) of the whole task in system. 
		- high modularity can be seen also as a sort of static redundancy (such as OOP). Only C not supported. 
	- dynamic redundancy: response to error through exception handling
		- [[programming language comparison in exception handling]]

### different software components: simultaneously active -> concurrency
- [[programming language comparison in concurrent tasks]]
- [[programming language comparison in shared variables]]
- [[programming language comparison in messages]]

Both C/POSIX and Java support concurrency. C on it’s own does not provide concurrency. Which can be a problem since not all real time systems have an OS. Both support concurrency by means of thread’s. The implementation is quite similar. A slight difference is that in Java there is the ‘new’ state in which a thread is created but not yet running. Threads should actively be started by the ‘start’ method. In C/POSIX this is not the case. After creation they immediately become eligible for execution. It is also not possible in C to assign arbitrary attributes to a thread while this is possible in Java. The main benefit of the Sequential language +OS approach is the compatibility between different languages, however the benefits of concurrent languages far outweigh this. (compiler can check a number of things, not always OS, one vision, more readable)

 

Synchronization: The threads in the concurrency model share a memory space. To prevent errors it’s important to synchronize functions so that shared memory spaces are not edited by two functions at the same time. To do this C/POSIX makes use of monitors. Monitors are a structured way to solve this problem and add the option to use a condition variable which prevents a function of accessing the shared memory if a condition is not met. Java actually also makes use of monitors, only not explicitly. They use the synchronized type, which makes sure that there’s only operation in mutual exclusion, to complete the monitor you can add a condition variable by using wait() and a while loop. Both are thus quite similar.

 

Messages: In C/POSIX messaging is done by asynchronous synchronization, symmetrical naming and a free message structure. Java on the contrary uses a remote procedure call or remote method invocation. Which basically means that the user doesn’t see what’s going on. Making it once again more abstract and easier to program but also more difficult to understand what’s going on exactly.

Atomic actions: Both do not explicitly support atomic actions, however the behavior can be obtained in both cases.

### dealing with  'time', real time control possibilities
- support for RT tasks
- scheduling


- real-time facilities (check in the book)
	- access to the clock
		- Ada: extensive clock package
		- C/POSIX: ANSI C has a type time, POSIX provides for a number of routines
		- Java: analogous to Ada
		- RTSJ: more extensive
	- programming of timeouts (cope with an expected action that does not occur, stop the code that is executing too long)
		- Ada: alternative in a select, timeout when sending
		- C/POSIX: timeouts on actions via signal `SIG_ALARM`
		- RTSJ: more extensive
	- [[temporal scopes]]


 

-   ●  Java real time explicitly has a different syntax for the real time part. Making it a clearer code. There’s a different thread type for real time threads that has some useful attributes that indicate for example when the deadline is etc.
    
-   ●  Java real time has special attributes for periodic behavior: PeriodicParameters extends ReleaseParameters. C/POSIX does not but can obtain the behavior by means of sleep() and clock_nanosleep().
    
-   ●  Aperiodic and sporadic activities: Java can limit the queue so that they are executed and not starved. C/POSIX does not have that option.
    
-   ●  Asynchronous events: Both support it in C/POSIX it’s called signals. Special handlers for this, C/POSIX uses resumption and Ada/Java uses termination.
    
-   ●  Scheduling: JavaRT contains a schedule class that provides for feasibility analysis, admission control, dispatching, and asynchronous event handling mechanism. Also support for priority inheritance, monitoring missed deadlines etc.

### interactions with hardware interface -> low level programming

0.  Java supports DMA and shared memory. RTJ views an interrupt as an asynchronous event. C is not made for device drivers (huh C is made to program UNIX, it is of course pretty error prone because lacking in high level concepts and checks) only through assembly in the code (example in slides/book is not assembly ... I think the compiler should offer ways to deal with registers by mapping them to address and then assembly is avoidable), however, accessing specific memory locations is more straightforward in C. Pff little to say about it...

 

○ C: (p. 517, chap 14 slide 19)  
■ Offers many low-level option. C is very close to hardware

○ Ada: (p. 504, chap 14 slide 22)  
■ Offers high level facilities.

○ Java: (p. 514, chap 14 slide 35)

-   RT Java introduces some facilities (in between C and Ada)
    
-   Can define different memory scopes (Immortal, Scoped, Heap, Physical)