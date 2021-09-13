```c
#include <pthread.h>

pthread_attr_t attributes;
pthread_t xp, yp, zp;

typedef enum {xplane, yplane, zplane} dimension;

int new_setting(dimension D);
void move_arm(dimension D, int P);

void controller(dimension *dim) {
	int position, setting;

	position = 0;
	while (1) {
		move_arm(*dim, position);
		setting = new_setting(*dim);
		position = position + setting;
	}
	// note, no call to pthread_exit, process does not treminate
}

#include <stdlib.h>
int main() {
	dimension X, Y, z;
	void *result;

	X = xplane;
	Y = yplane;
	Z = zplane;
	if (pthread_attr_init(&attributes) != 0)
		// set defaule attributes
		exit(EXIT_FAILURE);
	if (pthread_create(&xp, &attributes, 
					   (void *)controller, &X) != 0)
		exit(EXIT_FAILURE);
	if (pthread_create(&yp, &attributes, 
					   (void *)controller, &Y) != 0)
		exit(EXIT_FAILURE);
	if (pthread_create(&zp, &attributes, 
					   (void *)controller, &Z) != 0)
		exit(EXIT_FAILURE);
	pthread_join(xp, (void **)&result);

	// need to block main program

	exit(EXIT_FAILURE);
	// error exit, the program should not terminate
	// error condition exit(-1)
}
```

What is the role of the `exit` calls?  Why is `pthread_join` necessary? 
- A thread attribute object is created with the default attributes. Calls to `pthread_create` create each instance of the controller thread and pass a parameter indicating its domain of operation. If any errors are returned from the operating system, the program terminates by calling the `exit` routine. 
- Note that a program which terminates with threads still executing results in those threads being terminated. Hence it is necessary for the main program to issue a `pthread_join` system call even though the threads do not terminate. In other words,  `pthread_join` is needed as when a process terminates, all its threads are forced to terminate. 
- need `pthread_join` as when a process terminate, all its threads are forced to terminate