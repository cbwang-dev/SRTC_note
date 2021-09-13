0. summary
1. what is it? 
	1. Concurrent execution in Java is the execution of a process by several threads at the same time in the Java language. For example a big process is split in smaller tasks to be solved simultaneously, the solving of these tasks simultaneously is concurrent execution. Ada and Java offer these possibilities in the language while C requires intervention of the OS.
2. what does it do? 
	1. Solve different tasks simultaneously that might need to access/alter shared data in Java.
3. how does it work? 
	1. In Java there are two ways to create threads for concurrent execution. 
		1. A first option is to create a thread is to make a child class of the predefined `Thread` class. 
		2. And a second option is to declare a class that implements the `runnable` interface and is afterwards associated with the `Thread` class. Java threads need to be explicitly created and started.
		3. The second way more accurately defines the relationship between the new class and the thread class. The first way uses inheritance to obtain the new class, the second way uses object composition. Note that the second way can be more powerful, as Java doesn’t support multiple inheritance
	2. Java allows dynamic thread creation (Like Ada) and allows arbitrary data to be passed as parameters (Ada does not). There is no master or guardian concept (except for the main program which terminates when all user threads are terminated)
4. where is it used?
	1. In any application that needs to perform as fast as possible or which represents a real world problem that is also concurrent.
5. when is it used? 
	1. When speed of execution is important.
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros
		1. Better readable and maintainable code, the compiler can check a number of things, a language provides a single vision, one thoughtful way to address a problem, more portable for different OS, sometimes there is no OS so than (OS + seq language is no option).
		2. For Java, Dynamic thread creation, possibility to pass arbitrary data as parameters
	2. cons
		1. Hard to combine programs written in different languages
		2. on some operating systems it is difficult to implement concurrent languages.
8. what are the possible alternatives?
	1. Ada or [[concurrent execution in C POSIX]]