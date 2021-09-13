0. summary
1. what is it?
2. what does it do? 
	1. bring the system back in a previous consistent state
	2. then another part of the program (or a different version) is carried out and continue: **checkpointing**
3. how does it work? 
4. where is it used?
5. when is it used?
6. what are the potential problems? 
	1. checkpointing
		1. solution: consistent recovery lines
7. what are the pros and cons?
	1. pros
		1. one need to know the precise location of the fault
		2. maybe supported by the system, independent to application, separating of concerns
	2. cons
		1. cannot cancel actions (eg. sensor input in real time)
		2. cannot restore the damage (eg. wrongly launched the missile)
		3. can take a long time (especially save checkpoints)
		4. use lot of memory (especially save checkpoints)
8. what are the possible alternatives?
	1. [[forward recovery]]