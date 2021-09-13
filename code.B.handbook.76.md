```ada
generic
	Size : Natural := 100;
	type Item is private;
package Stack is
	Stack_Full, Stack_Empty : exception;
	procedure Push(X:in Item); procedure Pop(X:out Item);
end Stack;
	
package body Stack is
	type Stack_Index is new Integer range 0 .. Size-1;
	type Stack_Array is array(Stacked_Index) of Item;
	type Stack is
		record
			S  : Stack_Array;
			Sp : Stack_Index := 0;
		end record;
	Stk : Stack;

	procedure Push(X:in Item) is
	begin
		if Stk.Sp = Stack_Index'Last then
			raise Stack_Full;
		end if;
		Stk.Sp := Stk.Sp + 1;
		Stk.S(Stk.Sp) := X;
	end Push;

	procedure Pop(X:out Item) is
	begin
		if Stk.Sp = Stack_Index'First then
			raise Stack_Empty;
		end if;
		X := Stk.S(Stk.Sp);
		Stk.Sp := Stk.Sp - 1;
	end Pop;
end Stack;
```
It may be used as follows:
```ada
with Stack; with Text_Io;
procedure Use_Stack is
	package Integer_Stack is new Stack(Item => Integer);
	X : Integer;
	use Integer_Stack;
begin
	...
	Push(X);
	...
	Pop(X);
	...
exception
	when Stack_Full =>
		Text_Io.Put_Line("Stack Overflow");
	when Stack_Empty =>
		Text_Io.Put_Line("Stack Empty");
end Use_Stack;
```

**Question: Why are no exceptions caught in the routines of the package `Stack`?**

- Exceptions are caught in the initialization part of the package, if in the routine. 
- The stack is generic in that any object can be passed as a parameter to push. Hence, there is no need to instantiate the stack. 