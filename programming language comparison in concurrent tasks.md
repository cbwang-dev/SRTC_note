 

-   C: (p. 116, chap 4 slide 27)
    
    -   Threads not supported by language but by operating system
        
        through POSIX.
        
    -   Complicated, unreadable code, difficult to work with, no help
        
        from the compiler (Ada and Java have opposite advantages)
        
-   Ada: (p. 105)
    
    -   Explicit support of threads (=tasks)
        
    -   Tasks created implicitly on entry into declaration scope.
        
    -   Guardian(=master)/dependent concept - the block responsible
        
        for the termination of another task. The master cannot exit until
        
        all its dependents are terminated.
        
    -   Only discrete and pointer types can be passed as initialization
        
        parameter.
        
-   Java: (p. 111)
    
    -   Explicit support of threads as classes either extending Thread or implementing Runnable
        
    -   Created like any other object instance.
	-   No guardian concept (handled by Garbage collector)

	-   Can pass any data to the constructor