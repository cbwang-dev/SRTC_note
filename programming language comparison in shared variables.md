 

Shared variables: access to variables in common memory defining a critical

section where a task is guaranteed exclusive access (=mutual exclusion) and conditional synchronization.

-   C- Semaphores: (p. 145, chap 5 slide 61)
    
    -   Low-level mechanism
        
    -   Implementation treated below
        
    -   Can lead to starvation or deadlock and messy code - can lead
        
        to more errors.
        
    -   Mutual exclusion and conditional sync require 2 sets of
        
        semaphores.
        
    -   Can also be implemented in Java and Ada but bad idea
        
-   C- Monitors (p. 157, chap 5 slide 75)
    
    -   More structured way to implement mutual exclusion with
        
        conditional sync.
        
    -   Special module (=monitor) with critical sections in methods. All
        
        methods are exclusive to each other.
        
    -   Still rely on low-level semaphores - same disadvantages
        
    -   Only 1 reader or writer
        
-   Ada - Protected objects (p. 163, chap 5 slide 90)
    
    -   Structured abstraction of monitors.
        
    -   Implementation treated below
        
    -   Allows several readers or 1 writer
        
-   Java - Synchronized methods
    
    -   Protected objects similar to Ada but support inheritance
        
    -   Keyword synchronized labels a method as mutually exclusive
        
        with all synchronized methods.