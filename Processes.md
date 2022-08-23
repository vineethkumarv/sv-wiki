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


