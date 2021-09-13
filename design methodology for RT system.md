```
requirements
analysis
design
	architectural design
	detailed design
implementation
test
```

1. Requirements
	- both functional and non-functional
		- what it should do?
		- but also expected performance, security, reliability
	- outcome: specification document
		- preferably formal = in format that computer can manipulate
		- make possible to check things, but for this you have to be highly educated
2. Design (decomposition and abstraction)
	- decomposition: "divide and conquer" principle
		- systematically breaking down a complex problem into smaller and smaller entities, until components can be isolated
		- top down design
	- abstraction
		- to specify essence of components, gives possibility to add details in a later phase
		- bottom up design
	- Notations: classes and modules
		- UML is well known notation, is already part of "detailed design“
		- classes: for components in object oriented languages
		- modules: general widely used term for component
	- Metrics (ideally: strong cohesion, loose coupling)
		- cohesion
		- coupling
3. testing and simulation
	- component testing
	- often not possible to test in real environment
	- thus prefer simulation sometimes
		- restriction, can not match reality
		- costly