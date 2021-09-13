- definition of asynchronous events
	- Mechanism by which process A asks the attention of process B, without B explicitly waiting for message from A.
	- also called **signals**
- support for asynchronous events
	- [[resumption model]]
		- corresponds to a software interrupt, implemented in [[signals in POSIX]]
	- [[termination model]]
		- receiving process defines a domain within which it is prepared to receive asynchronous events. After handling event it will continue in another place
		- Ada and RTSJ support this
		- make run-time system more complicated
- need for asynchronous events
	- multi thread environment
	- sometimes a process must quickly react to certain events, polling or waiting is not appropriate
	- fault repair, supporting [[atomic action]]
	- changing of execution mode (change flight mode of a plane) can happen suddenly
	- calculations can be increasingly refined
		- some algorithms can get a better result with longer calculation time
		- asynchronous events scheduling determine the best calculation time
	- user interrupts (clicking the button that changes mode)
- alternative
	- message passing (eg. [[remote procedure call]])
	- communication through shared memory

flexible way of communication

[[programming language comparison in asychronous events]]