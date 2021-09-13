- What  
	- structured way to write code-segments that execute in mutual exclusion, and with possibility of conditional synchronization
- How  
	- module with a collection of critical sections, each written as a procedure or function
	- module is called monitor
	- all variables that must be protected are hidden (information hiding)
	- condition variables are used for conditional synchronization 
		- wait: blocks always the executing process  
		- signal: unblocks a waiting process if there is one
- comments
	- at least 2 processes, one producer (but there may be more than one) and one consumer (but there may be more than one)
	- processes can be blocked 
		- because they try to enter the monitor, they try to execute append or take
		- because they wait for a condition. e.g. there is no place in the buffer or there are no elements in the buffer
	- so there is a possible queue for the monitor itself and for each condition variable
- pro: structured way to program [[mutual exclusion]]
- con: low level way to program conditional synchronization

```ada
monitor buffer;  
	export append, take;  
	const size = 32;  
	var buf: array[0...size-1] of integer;
		top, base : 0 .. size-1;  
		SpaceAvailable, ItemAvailable : condition; 
		NumberInBuffer : integer;

	procedure append (I : integer) ..... 
	procedure take (var I : integer) .....

begin (* initialization *) 
	NumberInBuffer := 0; 
	top := 0;  
	base := 0;
end;

 

procedure append (I : integer); 
begin
	if (NumberInBuffer = size) then wait (SpaceAvailable); 
	buf[top] := I;  
	NumberInBuffer := NumberInBuffer + 1;  
	top := (top + 1) mod size;
	signal (ItemAvailable);  
end append;  

procedure take (var I : integer); 
begin
	if (NumberInBuffer = 0) then wait (ItemAvailable); 
	I := buf[base];  
	base := (base + 1) mod size;  
	NumberInBuffer := NumberInBuffer - 1;
	signal (SpaceAvailable); 
end take;

```