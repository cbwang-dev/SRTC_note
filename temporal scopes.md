A temporal scope is similar to normal scopes in the sense that it also has a domain in which its statements are valid and outside of that they no longer make sense. The domain is this time defined by a certain period in time. A temporal scope might have one or more of the following attributes:

- deadline
- minimum/maximum delay
- maximum execution time
- maximum elapsed time (between start and end of execution)

Temporal scopes are either periodic or aperiodic. Typically periodic temporal scope sample data or execute a control loop and aperiodic or sporadic (sporadic = aperiodic with min delay between events) temporal data arise from asynchronous events. In order for the statements to not go out of scope it’s important to have a good scheduler.

There is no real support from Ada or C/POSIX. In Java real time threads can be used that can have deadlines, missed deadlines can also be monitored in Java. In all languages a delay can be used for the minimum start time.