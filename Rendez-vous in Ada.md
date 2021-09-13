- main characteristics
	- synchronization model: [[non-local invocation]]
	- [[process naming]]: direct naming, asymmetrical naming
	- structure of message: free, comparable to parameters
- sending message
	- no new keyword or language construction
	- analogous to calling a procedure of a protected entry
- receiving message
	- declaration via `entry`
	- receiving via `accept`
- messages are more or less visible, which is different from [[remote procedure call]]. 
- pros and cons
	- pros: automatically queue requests
	- cons: quite low level
   
```ada
procedure Test;
	N: constant Integer := 1000;
	
	Task T1 is -- caller make an entry type
		entry Exchange(I: Integer; J: out Integer)
	end T1;
	
	Task body T1 is
	A, B: Integer;
	begin
		for K in 1 .. N loop
			-- produce A
			accept Exchange(I: Integer; J: out Integer) do
				J := A; B := I;
			end Exchange;
			-- consume B
		end loop;
	end T1;
	
	Task body T2 is
	C, D: Integer;
	begin
		for K in 1 .. N loop
			-- produce C
			T1.Exchange (C, D);
			-- consume D
		end loop;
	end T2;
begin
	null;
end Test;
```