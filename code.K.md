```c
#include <semaphore.h>

typedef enum {high, medium, low} priority_t;
typedef enum {false, true} boolean;

sem_t mutex; // used for mutual exclusive access to waiting and busy
sem_t cond[3]; // used for condition synchronization
int waiting; // count of numbers of threads waiting at a priority level
int busy; // indicates whether the resource is in use

void allocate(priority_t P)
{
	SEM_WAIT(&mutex); // lock mutex
	if(busy) {
		SEM_POST(&mutex); // release mutex
		SEM_WAIT(&cond[P]); // wait at correct priority level
		// resource has been allocated
	}
	busy = true;
	SEM_POST(&mutex); // release mutex
}

int deallocate(priority_t P)
{
	SEM_WAIT(&mutex); // lock mutex
	if(busy) {
		busy = false;
		// release highest priority waiting thread
		SEM_GETVALUE(&cond[high], &waiting);
		if( waiting < 0 ) { SEM_POST(&cond[high]); } 
		else {
			SEM_GETVALUE(&cond[medium], &waiting);
			if( waiting < 0 ) { SEM_POST(&cond[medium]); } 
			else {
				SEM_GETVALUE(&cond[low],&waiting);
				if( waiting < 0 ) { SEM_POST(&cond[low]); } 
				else SEM_POST(&mutex);
				// no one waiting, release lock
			} 
		}
		// resource and lock passed on to highest priority waiting thread
		return 0;
	}
	else return -1; // else return
}

void initialize() {
	priority_t i;

	busy = false;
	SEM_INIT(&mutex, 0, 1);
	for (i = high; i <= low; i++) {
		SEM_INIT(&cond[i], 0, 0);
	};
}
```

\pagebreak

What is the role of `MUTEX`?  

There are 3 conditional synchronization semaphores. What are they used for?  