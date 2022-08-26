# Processes
A Processes or Thread is any piece of code that gets executed as a separate entity. A fork-join block creates the different threads that run in parallel.

In the below figure we can see that types of processes and the process controls.

![Untitled Diagram drawio (2)](https://user-images.githubusercontent.com/110509375/186194367-81333f7f-a4f1-486c-800c-79606be624c3.png)

          Fig-1: The processes and process control blocks.

## Cheat sheet links
| **Processes**         | **Description** |
|:---------------------- | :-------------|
|[fork join](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#1fork-join)|Parent thread will execute when all child threads are over|
|[fork join_any](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#2fork-join_any)|Parent thread will be execute when anyone child thread gets over|
|[fork join_none](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#3-fork-join_none)|Parent thread executed parallel with child thread |
|[wait fork](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#1-wait-fork)|It allows the main process to wait until all the child thread process is over|
|[disable fork](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#disable-fork)|It terminate the all the execution when disable fork is execute|


## Processes or Threads
We have 3 types of Threads/Processes
1. fork-join
2.  fork-join_any
3.  fork-join_none

## 1.fork-join
SystemVerilog provides support for parallel threads through fork-join construct. In fork-join process parent thread will execute when all the child thread is finish the execution.  

**syntax**:-
  
**fork**  
   //Thread 1  
  //Thread 2  
  //Thread 3  
**join**  

In the below we can see that main thread 1 is executed first but main thread 2 is executed after all the child threads are executed and the child threads will execute according to the time delays.

![Untitled Diagram drawio (6)](https://user-images.githubusercontent.com/110509375/186889441-662c114e-ac91-4947-94c8-7c0f303c606c.png)

          Fig-2: The output of fork join block.
  
Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join/fork_join.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join/fork_join.log

## 2.fork-join_any  

The parent thread blocks will be execute when  any one of the child threads is finish the execution. It means if you have 2 or more thread in your fork..join_any block and each thread need different time to finish. In this case, whichever thread finished first, fork..join_any will comes out of the block and will start executing the next parent thread/statement in simulation. It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.  

 **syntax**:-
  
**fork**  
   // Thread 1 \
  // Thread 2 \
 // Thread 3  
**join_any**

In the below figure we can see that  here  main thread 1 executed and one child is executed and then main thread 2 is executed.If we have main thread and child thread has same delay then the child thread is executed first like here we can see thread 4-1  and main thread 2 has same time delay but thread 4-1(i.e child thread) executed first. 

![Untitled Diagram drawio (7)](https://user-images.githubusercontent.com/110509375/186891255-902be705-514f-46a5-b460-f49a7598c228.png)

          Fig-3: The output of fork join_any block.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.log

## 3. fork-join_none  

The parent thread is executed parallel with the child thread. This means the thread which is outside the fork-join_none, does not wait for the completion of any  threads which is inside the fork-join_none, it just execute parallel.  
It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.  
 **syntax**:-  
 
**fork**  
   // Thread 1 \
  // Thread 2 \
 // Thread 3  
 **join_none**   

In the below figure you can see that after the execution of main thread 1 we have same delays for main thread 2 and child thread (i.e thread 1) so here we can see that main thread 2 is executed first and then the child thread are executed and you can after executing child thread1 and thread 2 only we can see main thread 3 even though we have same delays so we can say that all the time child thread has the priority

![Untitled Diagram drawio (8)](https://user-images.githubusercontent.com/110509375/186891715-959c0d1d-3cfa-44cd-9b58-8ff957c8b85b.png)

          Fig-4: The output of the fork join_none block.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_none/fork_join_none.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_none/fork_join_none.log

-------------------------------------------------------------------------------------------------------------------------------------------------------
# **Process control**

SystemVerilog provides constructs that allow one process to terminate or wait for the completion of other processes. 
1. wait fork
2. disable fork  

## 1. wait fork  

The wait fork statement is used to ensure that all child processes (processes created by the calling process) have completed their execution.
it wait untill all the fork procersses complete the execution .  

In the below figure we see that the main thread 2 is executed after all the threads are executed even though we have the zero time delay for the main thread 2.it's because we have included the wait fork before the main thread 2 so it waits until the fork gets done.

![Untitled Diagram drawio (9)](https://user-images.githubusercontent.com/110509375/186892635-e4555220-2465-4c79-b5f1-856ec84194c8.png)

          Fig-5: The output of wait fork process control statement.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.sv

github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.log  

## 2. disable fork  

On execution of the disable fork, all the active process will get terminated.

In the below figure we can see that after execution of main thread 1 we will move the thread 1 (fork_join) but after the thread 1 execution when it hit by the disable fork it termiates the process and executes the main thread 2.

![Untitled Diagram drawio (10)](https://user-images.githubusercontent.com/110509375/186893331-6fd6670c-fcfc-400b-90e2-53846c9e7068.png)

          Fig-6: The output of disable fork process control statement.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/disable_fork/disable_fork.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/disable_fork/disable_fork.log