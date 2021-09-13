1. what is it, 
2. what does it do, 
3. how does it work, 
4. where is it used, 
5. when is it used, 
6. what are the potential problems, 
7. what are the pros and cons, 
	1. cons
		1. inappropriate for hard RT system, because deadline have possibilities to miss. Switch off when hard RT. 
8. what are the possible alternatives, etc.
	1. pointers in C (which is a sort of memory management, but leading to errors easily)



Service provided by the Java Virtual Machine for memory monitoring. Releases chunks of memory from the memory heap not being used. Programmer does not have to deallocate memory space - done automatically by GC. Can be problematic in Real-time application - GC non-predictable in time usage and what memory bits are deallocated. Solution: allocate RT threads in other than Heap memory types: Immortal (deallocated at the end of program), Scoped (deallocated at the end of lexical scope).