0. summary
1. what is it?
	1. A real-time system is a system that has to respond within a certain time limit. 
	2. 'real' points to difference with computer time: it is real because it is the external, actual time. 
	3. There are hard RT systems (that no longer work appropriately if a deadline is missed) and soft RT systems (still work if occasionally a deadline is missed). 
	4. You could also still subdivide in time aware (system refers to worldly clock) and reactive (system reacts on a certain event like user input).
	5. The correctness of the system depends not only on the logical result but also from the time when the result was given. As a result, not responding on time is as bad as wrong answers. 
2. what does it do? 
	1. A real time system can do all sorts of things. It gives an ‘output’. 
	2. This output can be the movement of an actuator but also some numbers on a screen. 
	3. It interprets the input and gives an output within the deadline.
3. how does it work? 
	1. Real time systems usually operate by using real time programming languages like Ada, Real time Java, and C/POSIX. These languages have special features like for example concurrency programming to ensure a response within the time frame.
4. where is it used?
	1. Control: controlling pipe flow by controlling the angle of a valve. 
	2. Communication: Skype  
	3. Command: Regulating the temperature in a room, stock trading operations
5. when is it used?
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros
		1. A fast response which is crucial for time critical applications
	2. cons
		1. Due to the strict deadlines, there is (most often) no time for a ‘human’ check of the result before something is done with it. For example the calculation of the distance to an object in a self-driving car. There’s no time to check it therefore the system itself should be as reliable as possible. Another disadvantage is that it requires specific programming languages that are capable to deal with the limitations imposed by a real-time problem. Due to these limitations the programs often get very complex.
8. what are the possible alternatives?
	1. Although communication, command and control is a military term, there is a wide range of disparate applications, which exhibit similar characteristics; for example, airline seat reservation, medical facilities for automatic patient care, air traffic control, remote bank accounting and large-scale manufacturing plants. Each of these time-aware systems consists of a complex set of policies, information gathering devices and administrative procedures which enable decisions to be supported, and provide the means by which they can be implemented. Often, the information gathering devices and the instruments required for implementing decisions are distributed over a wide geographical area.