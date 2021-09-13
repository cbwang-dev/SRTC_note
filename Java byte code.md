portable binary format  
instruction set for VM  
portable across platforms supporting Java  
source code translation is done in advance by java compiler  
faster than fully interpreted solution  
can be translated into machine language  
allow high level coding  

no direct access to hardware (no pointers, no byte code portion for accessing physical address)
size of code not compatible with embedded systems: JVM huge
byte code interpretation slower than C

the graph of where byte code is

 

-   compiled Java source code (written code) by Java compiler. Instructions to the Java Virtual Machine. Translated into object code (readable by hardware) by JVM:
	-   At each appearance - byte code interpreter, Classic JVM
	-   At first occurrence - just-in-time compiler
	-   Before loading - ahead-of-time compiler
    
Byte-code is portable across platforms, is faster than fully interpreted solution.