```ada
with Semaphore_Package; use Semaphore_Package;
separate (Main)
package body Buffer is
	Size : constant Natural := 32;
	type Buffer_Range is mod Size;
	Buf : array (Buffer_Range) of Integer;
	Top, Base : Buffer_Range := 0;

	Mutex : Semaphore; -- default is 1
	Item_Available : Semaphore(0);
	Space_Available : Semaphore(Initial => Size);

	procedure Append(I : Integer) is
	begin
		Wait(Space_Available);
		Wait(Mutex);
			Buf(Top) := I;
			Top := Top +1;
		Signal(Mutex);
		Signal(Item_Available);
	end Append;

	procedure Take (I : out Integer) is
	begin
		Wait(Item_Available);
		Wait(Mutex);
			I := Buf(Base);
			Base := Base + 1;
		Signal(Mutex);
		Signal(Space_Available);
	end Take;
end Buffer;
```

- `Mutex` is an ordinary [[mutual exclusion]] [[semaphore]] and is given default initial value of 1; 
- `Item_available` protects against taking from an empty buffer and had the initial value 0;
- `Space_availablable` (initially `Size`) is used to prevent `Append` operations to a full buffer. 

When the program starts, any consumer task that calls `Take` will be suspended on `Wait (Item_Available)`; only after a producer task has called `Append`, and in doing so `Signal(Item_Available)`, will the consumer task continue. 

Condition variables are used for conditional synchronization:
- wait: blocks always the executing process
- signal: unblocks a waiting process if there is one

How can this be done more easily in Ada?  

 

Extra: Although the semaphore is an elegant low-level synchronization primitive, a real-time program built only upon the use of semaphores in again error-prone. It needs just one occurrence of a semaphore to be omitted or misplaced for the entire program to collapse at run-time. Mutual exclusion may not be assured and deadlock may appear just when the software is dealing with a rare but critical event.