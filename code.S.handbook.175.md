```java
public class ReadersWriters{
	// prefereence is given to waiting writers
	public synchronized void startWrite() throws InterruptedException{
		// Wait until it is ok to write
		while(readers > 0 || writing){
			waitingWriters++;
			try{
				wait();
			} finally { waitingWriters--; }
		}
		writing = true;
	}
	public synchronized void stopWrite() {
		writing = false;
		notifyAll();
	}
	public synchronized void startRead() throws InterruptedException{
		// Wait until it is ok to read
		while(writing || waitingWriters > 0) wait();
		readers++;
	}
	public synchronized void stopRead() {
		readers--;
		if(readers == 0) notifyAll();
	}
	private int readers = 0;
	private int waitingWriters = 0;
	private boolean writing = false;
}
```

In this, many readers and many writers are attempting to access a large data structure. Readers can read concurrently, as they do not alter the data; however writers require [[mutual exclusion]] over the data both from other writers and from readers. There are different variations on this scheme; **the one considered here is where priority is always given to waiting writers.** Or, In this code the **writers** get the advantage and priority. Hence, as soon as a writer is available, all new readers will be blocked until all writers have finished. Of course, in extreme situations this may lead to [[starvation]] of readers. 

When `startWrite()` is accessed, first of all it is checked whether the lock `writing` is free and the condition variable `readers` is zero. If this is not the case then the while loop is entered and the thread is added to a waiting list of threads. The counter ``waitingWriters`` is incremented by one. If a thread is finished writing or the last thread is finished reading then `notify_all()` is called. This wakes up all waiting threads. The thread gets out of the `wait()` loop and diminishes `waitingWriters` by one. Then it checks its condition variable (`readers`) and the lock (`writing`) once again. If `readers` is zero and the lock (`writing`) is free then the thread acquires the lock and starts writing. After a while the thread is done and the procedure `stopWrite()` is called. The lock(`writing`) is freed and all waiting threads or readers are notified.

When `startRead()` is called, first of all it is checked whether there are waiting writers and the lock (`writing`) is free. If the lock is free and there are no waiting writers then the counter `readers` is incremented by one and the function starts reading. Afterwards `stopRead()` is called. The counter `readers` is diminished by one. If the counter `readers` is zero right now then `notifyAll()` is called to notify all waiting threads.

In this solution, on awaking after the wait request, the thread must re-evaluate the conditions under which it can proceed. Although this approach will allow multiple readers or a single writer, arguably it is inefficient, as all threads are woken up every time the data becomes available. Many of these threads, when they finally gain access to the monitor, will find that they still cannot continue and therefore will have to wait again.

