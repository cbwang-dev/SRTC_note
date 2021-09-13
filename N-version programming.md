0. summary
1. what is it?
	1. it is a method for achieving fault tolerance by using software redundancy (static)
2. what does it do? 
3. how does it work? 
	1. it design N independent piece of redundant software which are equivalent based on the same specifications. By introducing the diversity of design and voting for the final result, it can tolerate faults in different piece of sub systems. 
4. where is it used?
	1. it is used for hiding design-faults
5. when is it used?
	1. when fault tolerance is required by manipulating software. 
6. what are the potential problems? 
	1. answers possibly do not come at once, some versions might be slower
	2. comparing results
		1. integer is not a problem
		2. different precision
		3. voting when all solutions are basically good
7. what are the pros and cons?
	1. pros
	2. cons
		1. versions might not independent
		2. specification might be wrong (incomplete, inconsistent, ambiguous specifications)
		3. N-times the develop budget (all budget for one version might be better)
		4. difficult to compare results (voting)
		5. redundant components always run, waste of execution resources. That is because of the static nature, which is different from dynamic software redundancy. 
8. what are the possible alternatives?
	1. [[recovery blocks (dynamic software redundancy)]]