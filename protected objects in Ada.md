0. summary
1. what is it?
	1. A protected object is a type of object that can only be accessed under [[mutual exclusion]] conditions.
2. what does it do? 
	1. It assures that shared data is only manipulated by one thread at a time.
3. how does it work? 
	1. It works similarly to [[monitor in C POSIX]], the only difference here is that there are always multiple readers allowed at the same instance.
	2. functioning
		1. Acquire lock ([[guard in Ada]])
		2. Test condition variable 
			1. if true execute, notify and release lock (not always a condition present)	
		3. Release lock
		4. Wait until notified
		5. Acquire lock
		6. Test condition variable if true execute, notify and release lock
		7. Release lock and go back to step 4.
	3. For protected entries there’s another boolean expression or barrier inside the body of the protected object. Tasks are not suspended if they can’t access due to the data being in use but they are suspended and put in a queue when the condition or boolean expression is false. This is not possible for protected function calls! Protected function calls can execute with multiple at the same time (all readers)
4. where is it used?
	1. in concurrent programs
5. when is it used?
	1. whenever two or more threads share data
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros
	2. cons
8. what are the possible alternatives?
	1. [[monitor in C POSIX]]
	2. conditional critical sections for conditional synchronization
	3. synchronization (Java)