0. summary
1. what is it?
	1. a piece of redundant code that is executed when an exception (or error) is caught
2. what does it do? 
	1. It’s a form of dynamic [[forward recovery]]. An error occurs and the handler executes another piece of code and afterwards the program goes on. Where the program continues depends on whether it is a [[resumption model]] or a [[termination model]].
3. how does it work? 
	1. After each block of code you place an exception handler, you can specify which type of exception the handler should handle. If an exception occurs then ‘an exception is thrown’ and the exception handler block will execute. 
	2. In Java you need to encapsulate the code block by a try block
	3. in Ada this is not necessary
	4. C does not provide exception handling. Could be implemented through library, but a source of error than a solution
4. where is it used?
	1. In all code that needs to be reliable.
5. when is it used?
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros
		1. increase reliability
	2. cons
		1. Where to continue?
		2. cost space for redundant code
8. what are the possible alternatives?
	1. [[N-version programming]]
	2. [[recovery blocks (dynamic software redundancy)]]

[[programming language comparison in exception handling]]