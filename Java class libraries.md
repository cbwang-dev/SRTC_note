1. What is it: 
	1. Dynamically loadable libraries that provides an API that java applications can use during runtime. 
2. What does it do: 
	1. It allows the programmer to abstract implementations and use pre defined functions.
3. How does it work: 
	1. Since java doesn’t depend on a specific OS it can’t use the platform-native libraries, so that’s why java class libraries are implemented to be interpreted together with bytecode by the JVM. 
4. Where it is used: 
	1. In java code, often to solve frequently encountered problems (networking, multitasking, GUI, ...).
5. When it is used: 
	1. When you need to use a function from the libraries.  
6. What are the potential problems:
7. What are advantages and disadvantages: 
	1. The advantages are that:
		1.  it allows for a **higher abstraction** resulting in more readable code with possibly less chance of errors increasing the reliability. 
		2.  it has standard APIs, which increase portability of applications and lower cost of programming. 
		3.  it has support for multitasking, networking, and GUI. 
		4.  support Java to be "write once, run anywhere" (if same set classes are available)
	2.  The disadvantages are that:
		1.  The size of the library is large (up to 15 Mb), make it less promising for [[embedded systems]]. 
8. What are possible alternatives: 
	1. C code ada code or 
	2. implementing the functionalities yourself. 

chapter 1 slide 73