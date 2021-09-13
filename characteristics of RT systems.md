1. dealing with  'time', real time control possibilities
	1. response time is very important
	2. deadlines must be met in all circumstances
		1. worst-case should be known
		2. predictability of response time is critical
		3. real time systems are always over-dimensioned
	3. programming languages and OS must allow
		1. to specify time and deadlines, to react when a deadline is not met, to support periodic tasks, to control jitter
	4. Ch9-Ch12
2. different software components: simultaneously active
	1. all around us is simultaneously active
	2. on this simultaneity is best responded by simultaneously executing software components
	3. more and more real-time systems are distributed systems
	4. not good for this to be solved by programmers
		1. simultaneity not relevant to the problem, too complicated
		2. programs become obscure
		3. placement of additional code is difficult
		4. correctness proofs are very difficult ...
		5. (see book for even more difficulties)
	5. asks support of programming languages and/or systems
		1. modern programming languages offer this: Ada, Java, C#
	6. is covered in Ch4-6, and also Ch7-8
3. interactions with hardware interface
	1. connected hardware: often not the classic peripherals
	2. peripherals are interfaced
		1. via registers, interrupts
		2. preferably not through low-level programming
	3. is covered in Ch14
4. requirement for efficient implementation
	1. time requirements can be so severe 
		1. that efficiency is really important
	2. is not explicitly treated in this course
5. manipulation of real numbers (for you to read)
	1. many RT systems control an industrial activity
	2. e.g.: controller based on feedback
		1. controlled entity has a vector of output variables, which change over time
		2. outputs are compared with the desired signal
		3. difference is used to adjust the input variables
	3. control is based on mathematical model of process
		1. is complex, often based on differential equations
		2. (not covered in this book, nor in this course)
	4. discipline: control theory, system theory, control technology
6. large and complex
	1. not just proportional to the number of lines of code
	2. related to the variety in the code
	3. changes continuously because the environment changes
		1. continuously situations change
		2. change of needs
		3. need for continuous maintenance
	4. can vary from a few hundreds of lines assembler or C, up to 20 million lines Ada code (for the space station)
	5. domain of Software Engineering; modern languages try to handle this
	6. is not explicitly covered in this book or in this course
7. extremely reliable and secure
	1. more and more vital functions in society are entrusted to computer systems
		1. poorly functioning systems can be catastrophical
		2. often human lives are involved
			1. e.g. nuclear power stations	
			2. e.g. autonomous vehicles
		3. can also be extremely costly
	2. examples of very costly failure: at beginning of Ch2
	3. is treated in Ch2-3, Ch7, Ch13