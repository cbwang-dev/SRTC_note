[[asynchronous events]] can do fault repair of atomic action

- requirements for atomic actions
	- well-defined boundaries: start, end and side borders
		- can help to do [[backward recovery]]
	- isolation
		- an atomic action must not allow the exchange of any atomic action should have a start, an end and information between the tasks active inside the action and those outside (resource managers excluded).
	- strict nesting
		- two structures are strictly nested if one is completely contained within the other)
	- concurrency
		- implied synchronization at the end of an atomic action