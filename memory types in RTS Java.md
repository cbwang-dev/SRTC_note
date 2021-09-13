 

p. 523, chap 14 slide 37
 

1. Heap memory: normal Java. Handled by garbage collector.
2. Immortal memory: Shared among all threads of application. No garbage collection, freed when program terminates.
3. Scoped memory: Memory area where objects with well-defined lifetime can be allocated (lifetime = lexical scope). Can be entered explicitly (enter() method) or implicitly (attached to RealtimeThread at creation). Can be nested.
4. Physical memory: mapping to physical addresses. Can be immortal or scoped.