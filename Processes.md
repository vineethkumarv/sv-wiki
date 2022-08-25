# Processes
A Processes or Thread is any piece of code that gets executed as a separate entity. A fork-join block creates the different threads that run in parallel.

![Untitled Diagram drawio (2)](https://user-images.githubusercontent.com/110509375/186194367-81333f7f-a4f1-486c-800c-79606be624c3.png)


## Processes or Threads
We have 3 types of Threads/Processes
 1. fork-join
1.  fork-join_any
1.  fork-join_none
## 1.fork-join
SystemVerilog provides support for parallel threads through fork-join construct. Fork-join will start all the processes inside it parallely and wait for the completion of all the processes.
### syntax
#### fork 
   // Thread 1 \
  // Thread 2 \
 // Thread 3
#### join
## 2.fork-join_any
The parent thread blocks will be execute when  any one of the child threads is finish the execution. It means if you have 2 or more process in your fork..join_any block and each thread need different time to finish. In this case, whichever thread finished first, fork..join_any will comes out of the block and will start executing the next parent thread/statement in simulation. It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background


