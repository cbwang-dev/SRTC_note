```Java
public class FullStackException extends Exception {
	public FullStackException() {
	}
}

public class EmptyStackException extends Exception {
	public EmptyStackException() {
	}
}
	
public class Stack {
	public Stack(int capacity) {
		stackArray = new Object[capacity];
		stackIndex = 0;
		stackCapacity = capacity;
	}
	public void push(Object item) throws FullStackException {
		if(stackIndex == stackCapacity) throw new FullStackException();
		stackArray[stackIndex++] = item;
	}
	public synchronized Object pop() throws EmptyStackException {
		if(stackIndex == 0) throw new EmptyStackException();
		return stackArray[--stackIndex];
	}
	protected Object stackArray[];
	protected int stackIndex;
	protected int stackCapacity;
}

public class UseStack {
	public static void main(...) {
		Stack S = new Stack(100);
		try {
			...
			S.push(SomeObject);
			...
			SomeObject = S.pop();
			...
		}
		catch (FullStackException  F) {...}
		catch (EmptyStackException E) {...}
	}
}
```


Why are no exceptions caught in the routines of the package `Stack`?

why are the exceptions caught only at the bottom of the page?  



Already discussed below how does the exception handling works in Java. There was also a question in the exam that why does the function just throws the exception but not handle it there - we just handle it in the main’s catch block.  

So when we have an exception we can decide that we want to handle it there or throw it to an upper level. In this case it would have no sense to handle it in the function because our point is not the information that we have a `FullStackException` / `EmptyStackException` - the useful information that where do we use the code in a wrong way where we cause a `FullStackException` - and it will be on the main when we call the `S.push()` function more than we should. This is called Exception propagation.