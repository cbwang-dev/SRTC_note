0. summary
	1. has variations of [[binary semaphores]] and [[quantity semaphores]]
	2. analogous to traffic light
1. what is it?
	1. low-level mechanisms for synchronization purposes
2. what does it do? 
	1. ensure [[mutual exclusion]] and conditional synchronization
	2. control access to a common resource used by multiple processes in a concurrent system
3. how does it work? 
4. where is it used?
5. when is it used?
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros
		1. no need busy/wait protocols, such that it is error-prone
	2. cons: easily lead to errors thus not suitable for RT system
		1. leading to possible [[starvation]] and [[deadlock]] (contains example of deadlock in semaphore)
		2. too low level, leading to human error; in pairs, but compiler cannot check because not part of language
		3. hard to detect bugs
8. what are the possible alternatives?
	1. [[monitor in C POSIX]]
	2. [[protected objects in Ada]]
	3. synchronized methods in Java 

code example in Ada: (Ada does not directly support semaphore, but through `wait` and `signal` procedure, semaphore can be constructed in Ada)
```ada
package Semaphore_Package is
	type Semaphore(Initial : Natural := 1) is limited private;
	procedure Wait (S : in out Semaphore);
	procedure Signal (S: in out Semaphore);
private
	type Semaphore is ...
end Semaphore_Package;
```

