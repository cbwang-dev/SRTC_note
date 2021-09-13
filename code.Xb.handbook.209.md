```c
int main(int argc, char **argv) {
	mqd_t mq_xplane, mq_yplane, mq_zplane;
	/* one queue for each process*/
	struct mq_attr ma; // queue attributes
	int xpid, ypid, zpid;
	char buf[DEFAULT_NBYTES];
	
		/* set the required message queue attributes*/
		ma.mq_flags = 0;
		ma.mq_maxmsg = 1;
		ma.mq_msgsize = nbytes;
		
		/* calls to set the actual attributes for the three message queues*/
		mq_xplane = MQ_OPEN(MQ_XPLANE, O_CREAT|O_EXCL, MODE, &ma);
		mq_yplane = MQ_OPEN(MQ_YPLANE, O_CREAT|O_EXCL, MODE, &ma);
		mq_zplane = MQ_OPEN(MQ_ZPLANE, O_CREAT|O_EXCL, MODE, &ma);
		
		/* duplicate the process to get the three controllers*/
		switch (xpid = FORK()) {
			case 0: // child
				controller(xplane);
				exit(0);
			default: // parent
				switch (ypid = FORK()) {
					case 0: // child
						controller(yplane);
						exit(0);
					default: // parent
						switch (zpid = FORK()) {
							case 0: // child
								controller(zplane);
								exit(0);
							default: // parent
								break;
						}
				}
		}
		while (1) {
		/* find new position and set up buffer to transmit each*/
		/* coordinate to the controller, for example*/
		MQ_SEND(mq_xplane, &buf(0), nbytes, 0);
		}
}
```

what does the code do? What does "FORK()" do, why is it necessary?

the simple robot arm is sketched with a parent process forking three `controllers`. This time, the parent communicates with the controllers to pass them the new position of the arm. First the `controller` code is given. Here, `MQ_OPEN` and `FORK` are assumed to be functions which test the error return from the `mq_open` and `fork` system calls and only return if the calls are successful.