# Processes
A Processes or Thread is any piece of code that gets executed as a separate entity. A fork-join block creates the different threads that run in parallel.

![Untitled Diagram drawio (2)](https://user-images.githubusercontent.com/110509375/186194367-81333f7f-a4f1-486c-800c-79606be624c3.png)
## Cheat sheet links
| **Processes**         | **Description** |
|:---------------------- | :-------------|
|[fork_join](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#1fork-join)|Finishes when all child threads are over|
|[fork_join_any](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#2fork-join_any)|Finishes when any child thread gets over|
|[fork_join_none](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#3-fork-join_none)|Finishes soon after child threads are spawned|
|[wait_fork](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#wait-fork)|It allows the main process to wait until all the forked process is over|
|[disable_fork](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#disable-fork)||


## Processes or Threads
We have 3 types of Threads/Processes
 1. fork-join
1.  fork-join_any
1.  fork-join_none
## 1.fork-join
SystemVerilog provides support for parallel threads through fork-join construct. In fork-join process parent thread will execute when all the child thread is finish the execution .
### syntax
#### fork 
   // Thread 1 \
  // Thread 2 \
 // Thread 3
#### join
Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join/fork_join.sv

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join/fork_join.log

## 2.fork-join_any
The parent thread blocks will be execute when  any one of the child threads is finish the execution. It means if you have 2 or more thread in your fork..join_any block and each thread need different time to finish. In this case, whichever thread finished first, fork..join_any will comes out of the block and will start executing the next parent thread/statement in simulation. It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.
### syntax
#### fork 
   // Thread 1 \
  // Thread 2 \
 // Thread 3
#### join_any

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.sv

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.log

## 3. fork-join_none
The parent thread is executed parallel with the child thread. This means the thread which is outside the fork-join_none, does not wait for the completion of any  threads which is inside the fork-join_none, it just execute parallel.  
It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.  
### syntax
#### fork 
   // Thread 1 \
  // Thread 2 \
 // Thread 3
#### join_none

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_none/fork_join_none.sv

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_none/fork_join_none.log

-------------------------------------------------------------------------------------------------------------------------------------------------------
# **Process control**
SystemVerilog provides constructs that allow one process to terminate or wait for the completion of other processes. 
* wait fork
* disable fork
## wait fork
The wait fork statement is used to ensure that all child processes (processes created by the calling process) have completed their execution.
it wait untill all the fork procersses complete the execution .  

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.sv

github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.log
## disable fork
Terminate all child thread below the current contest level.