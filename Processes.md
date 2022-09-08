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
|[disable fork](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Processes/#2-disable-fork)|It terminate the all the execution when disable fork is execute|


## Processes or Threads
We have 3 types of Threads/Processes
1. fork-join
2.  fork-join_any
3.  fork-join_none

## 1.fork-join
SystemVerilog provides support for parallel threads through fork-join construct. In fork-join process parent thread will execute when all the child thread is finish the execution.  

**syntax**:-
  
`fork`  
   `Thread 1`  
   `Thread 2`  
   `Thread 3`  
`join`

**code snippet**:-  

    fork:FORK_F1  
      
      begin:BEGIN_B2  
        #1 a <= b;  
        b <= 7;  
        $monitor("[%0t] Thread-T2: Values of a= %0d,b= %0d, c= %0d,d= %0d",$time,a,b,c,d);  
        #1 ->e1;  
        c = b;  
      end:BEGIN_B2  
    
      begin:BEGIN_B3  
        wait(e1.triggered);  
        $display("[%0t] Event is triggered",$time);       
    
        begin:BEGIN_B4 //Thread 4  
          #1 d = c;           
        end:BEGIN_B4  

      end:BEGIN_B3  
    join:FORK_F1

In the below we can see that main thread 1 is executed first but main thread 2 is executed after all the child threads are executed and the child threads will execute according to the time delays.  


![Untitled Diagram drawio (24)](https://user-images.githubusercontent.com/110509375/188844965-ace54ff5-bc1a-4837-a9d1-8180d82822e2.png)


          Fig-2: The output of fork join block.

In the below fig you can easily understand how the entire code for fork-join works with respect to regions.  
where sampling of the variables will be done in preponed region.  
All the blocking assignments will be executed and all non-blocking assignments was evaluated in active region.  
$display statements will be executed in active region.  
All #0 delays statements will be executed in inactive region.  
The evaluated non-blocking assignments will be executed in NBA region.
$monitor statements will be executed in postponed region.

![fork_join](https://user-images.githubusercontent.com/110411714/188447939-537320d2-c8a8-4266-9b40-0f343427d743.png)

          Fig : scheduler Schematic for fork-join block.
  
Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/tree/b7_Team_BJT/processes/fork_join

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join/fork_join.log

## 2.fork-join_any  

The parent thread blocks will be execute when  any one of the child threads is finish the execution. It means if you have 2 or more thread in your fork..join_any block and each thread need different time to finish. In this case, whichever thread finished first, fork..join_any will comes out of the block and will start executing the next parent thread/statement in simulation. It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.  

 **syntax**:-
  
`fork  `  
   `Thread 1 `  
   `Thread 2 `  
   `Thread 3  `  
`join_any`  
 
 **code snippet**:
 
    fork:FORK_F1  
      
      begin:BEGIN_B2//Thread 1  
        #0 $display("[%0t] Thread_T2: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);      
        
        begin:BEGIN_B3  
          b <= a;  
          #1 $display("[%0t] Thread_T3: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);  
        end:BEGIN_B3  
      
      end:BEGIN_B2  
      
      fork:FORK_F2//Thread 2  
        
        begin:BEGIN_B4  
          #3 -> e1;  
          $display("[%0t] Thread_T4: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);  
        end:BEGIN_B4  
          
      join:FORK_F2  
      
    join_any:FORK_F1

In the below figure we can see that  here  main thread 1 executed and one child is executed and then main thread 2 is executed. 

![Untitled Diagram drawio (23)](https://user-images.githubusercontent.com/110509375/188843990-76f70d10-6f12-4cd7-8e1f-aa799d0a35b4.png)


          Fig-3: The output of fork join_any block.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/fork_join_any/fork_join_any.log

## 3. fork-join_none  

The parent thread is executed parallel with the child thread. This means the thread which is outside the fork-join_none, does not wait for the completion of any  threads which is inside the fork-join_none, it just execute parallel.  
It does not mean that the rest of the child threads will be automatically discarded by simulation. Those threads will be running in the background.  
 **syntax**:-  
 
`fork `  
  `Thread 1`  
  `Thread 2`  
  `Thread 3`  
`join_none`
 
**code snippet**:

    fork:FORK_F1  
      
      begin:BEGIN_B2  
        #1 $display("[%0t] Thread_T2: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);      
        b <= a;  
        #1 $display("[%0t] Thread_T3: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);  
      end:BEGIN_B2  
      
      fork:FORK_F2  
        #1 -> e1;  
        $display("[%0t] Thread_T4: Values of a =%0s,b =%0s,c =%0s,d =%0s",$time,a,b,c,d);  
      join:FORK_F2  
      
    join_none:FORK_F1

**Output**:


![Untitled Diagram drawio (28)](https://user-images.githubusercontent.com/110509375/189041598-f078d9c4-1eb0-40a2-bd4f-4c56c2060815.png)



          Fig-4: The output of the fork join_none block.

![Untitled Diagram drawio (14)](https://user-images.githubusercontent.com/110509375/188595513-afc52f87-fdf7-43d5-9211-f5da54b4cde0.png)


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
 
**code snippet**:

    fork:FORK_F1 //Thread 2  
    
      #2 b <= "Delta";//T2-1  

      #0 $display("[%0t] Thread_T2: values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
                
      begin:BEGIN_B2 //Thread 2-3  
        #1 -> e1;  
        c = "Hoode";  
        #1 $display("[%0t] Thread_T3: values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
      end:BEGIN_B2  
      
      fork:FORK_F2 //Thread 2-4  
        wait(e1.triggered);  
        #2 $display("[%0t] Thread_T4: values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
      join:FORK_F2  
      
      #1 $display("[%0t] Thread_T5: values of a = %0s,b = %0s,c = %0s",$time,a,b,c);//Thread 3  

    join_none:FORK_F1  
    
    wait fork;  
    #0 $monitor("[%0t] Thread_T6: values of a = %0s,b = %0s,c = %0s",$time,a,b,c);//Thread 6
   

In the below figure we see that the main thread 2 is executed after all the threads are executed even though we have the zero time delay for the main thread 2.it's because we have included the wait fork before the main thread 2 so it waits until the fork gets done.

![Untitled Diagram drawio (26)](https://user-images.githubusercontent.com/110509375/188847768-05f17aa2-0a50-4098-8550-1ee0e8042940.png)


          Fig-5: The output of wait fork process control statement.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.sv

github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/wait_fork/wait_fork.log  

## 2. disable fork  

On execution of the disable fork, all the active process will get terminated.

**code snippet**:

    fork:FORK_F1  
      
      #3 b <= "Delta";//Thread 1  
      
      #4 $display("[%0t] Thread_T2: Values of a = %0s,b = %0s,c = %0s",$time,a,b,c);//Thread 2  
             
      begin:BEGIN_B2 //Thread 3  
        #1 -> e1;  
        c = "Hoode";  
        #1 $display("[%0t] Thread_T3: Values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
      end:BEGIN_B2  
      
      fork:FORK_F2 //Thread 4  
          @(e1.triggered);  
          #1 $display("[%0t] Thread_T4: Values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
      join:FORK_F2  
      
      #1 $display("[%0t] Thread_T5: Values of a = %0s,b = %0s,c = %0s",$time,a,b,c);  
      
    join_any:FORK_F1  

    disable fork;  
    #1 $display("[%0t] Thread_T6: ending of fork-join",$time);   


In the below figure we can see that after execution of main thread 1 we will move the thread 1 (fork_join) but after the thread 1 execution when it hit by the disable fork it termiates the process and executes the main thread 2.

![Untitled Diagram drawio (27)](https://user-images.githubusercontent.com/110509375/188848545-5829b97b-d033-4fcf-8fb0-8a507c970f64.png)


          Fig-6: The output of disable fork process control statement.

Github lab link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/disable_fork/disable_fork.sv

Github log_file link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/processes/disable_fork/disable_fork.log