# Fine Grain Process Control

Systemverilog has a built in class named Process that allows one process(i.e, like fork_join) to access and control the processes/threads. When we fork off any thread, a new object of process class is created at that time. This object contains status information about that thread.  

![Untitled Diagram drawio (5)](https://user-images.githubusercontent.com/110509375/186867756-112267e1-547f-4882-8561-b04bcbd63805.png)

          Fig-1: These are all the pre-defined methods which are available in fine grain process control.

## Cheat sheet of different fine-grain process control:

|**S.no**|      **Tasks**         |     **Description**  |
|:-------|:---------------------- | :--------------------|
|1.|[self()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control#1self)|Used to will create the ID/object of the process.|
|2.|[status()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#2status)|Used to will return the mode of the current Thread.|
|3.|[kill()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#3kill)|Used to will kill the Thread.|
|4.|[await()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#4await)|Used to wait the current Thread for some other Thread to complete.|
|5.|[suspend()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#5suspend)|Used to suspend the Thread for some indefinite time.|
|6.|[resume()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#6resume)|Used to resume the Thread from suspended state.|

## 1.self()  

It creates the object/ID for process class. The object is used to access all the pre-defined methods of the process class.  
The object contains the Status information of all the Threads.    

**Syntax**:-  
`process p_handle1,p_handle2;`  
`initial begin`  
   `p_handle1 = process :: self();`  
   `p_handle2 = process :: self();`  
`end`  

**code snippet**:-  
```
fork:FORK_F1  

   $display("[%0t] Entered into fork-join and started first check for the process",$time);  
   #1 ->e1;  

   begin:BEGIN_B2  
      wait(e1.triggered);  
      if(p1 == null)  
         $display("[%0t] Not created",$time);  
      else  
         $display("[%0t] Created",$time);  
      ->e3;  
      #1 ->e2;  
   end:BEGIN_B2  

   #2 p1 = process :: self();  

   begin:BEGIN_B3  
      wait(e2.triggered);
      $display("[%0t] Started second check for the process",$time);  
      if(p1 == null)
         $display("[%0t] Not created",$time);
      else
         $display("[%0t] Created",$time);
      ->e4;
   end:BEGIN_B3
      
   fork:FORK_F2

      begin:BEGIN_B4
         wait(e3.triggered);
         $display("[%0t] first check for the process done",$time);
      end:BEGIN_B4

      begin:BEGIN_B5
         wait(e4.triggered);
         $display("[%0t] Second check for the process done",$time);
      end:BEGIN_B5
      
   join:FORK_F2

join:FORK_F1
```

In the above code snippet you can see that At #0 simulation time the handle for the process class was declared.  
In the below Fig-2,  
* At #1 simulation timewe are checking whether an object p1 was created or not then it was displaying **Not created**.  
* At #2 simulation time we are creating an object for the process p1.  
* At #3 simulation time we are checking for the object p1 it was displaying **Created**.  

![fine_self_output](https://user-images.githubusercontent.com/110447489/189285742-8b5f6e52-6100-485f-9ab0-5fcd7ec0b8e7.png)

          Fig-2: The output of the self() method.  

![fork join_any _self _kill-Page-2 drawio (3)](https://user-images.githubusercontent.com/110447489/189513905-7a604023-250b-44ca-9102-ceb11a9781ac.png)  

               Fig-3: scheduler Schematic for self() code.




Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.log

## 2.Status()  

It will shows the status/mode of the process ID. There are different modes like Finished, Running, Waiting, Suspended, Killed.  

**Syntax**:-  
`process p_handle;`  
`initial begin`  
   `begin`  
      `p_handle = process :: self();`  
      `$display("status : %s",p_handle.status());`  
   `end`  
`end`  

**code snippet**:-  
```
$display("[%0t] Seeking status:",$time);  

fork:FORK_F1  

   begin:BEGIN_B2  
      p1 = process :: self();  
      #1 $display("[%0t] I am in process p1",$time);  
      $display("[%0t] Initial status of p1: %s",$time,p1.status());  
      #1 $display("[%0t] Still working in p1",$time);  
      ->e1;  
      ->e2;  
   end:BEGIN_B2  
 
   begin:BEGIN_B3  
      p2 = process :: self();  
      wait(e2.triggered);  
      #1 $display("[%0t] I am in process p2",$time);  
      $display("[%0t] Initial status of p2: %s",$time,p2.status());  
      $display("[%0t] Still working in p2",$time);  
      ->e3;  
   end:BEGIN_B3  

   begin:BEGIN_B4  
      wait(e1.triggered);  
      $display("[%0t] Final status of p1: %s",$time,p1.status());  
   end:BEGIN_B4  

   begin:BEGIN_B5  
      wait(e3.triggered);  
      $display("[%0t] Final status of p2: %s",$time,p2.status());  
   end:BEGIN_B5  

   fork:FORK_F2  
      p3 = process :: self();  
      #1 $display("[%0t] I am in process p3",$time);  
      #1 $display("[%0t] status of p3: %s",$time,p3.status());  
      #1 ->e4;  
   join:FORK_F2  

join_any:FORK_F1  

wait(e4.triggered);  
#1 $display("[%0t] Final status of p3: %s",$time,p3.status());  
```

In the below Fig-4,  
* you can see that there are some strings which are in upper-case those are the status of a process p1 and p2.  
* At different simulation times the status of the processes/Threads will be changing depending on their execution.

![fine_status_output](https://user-images.githubusercontent.com/110447489/189286908-b4bc1409-e237-4720-a8eb-b4516aae7215.png)

          Fig-4: The output of the status() method.  

![status drawio (1)](https://user-images.githubusercontent.com/110447489/189482980-92a4d5af-bdf5-4b76-8a68-d425a9f97e7d.png)  

                         Fig-5: scheduler Schematic for status() method.



Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.log  

## 3.kill()  

The kill () function terminates the process and all its sub-processes. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be terminated in the current timestamp.  

**Syntax**:-  
`Process p_handle1;`  
`initial begin`  
   `fork`  
      `p_handle1 = process :: self();`  
      `p_handle1.kill();`  
   `join_any`  
`end`  

**code snippet**:-  
```
$display("[%0t] Seeking status:",$time);

fork:FORK_F1  

   begin:BEGIN_B2  
      p1 = process :: self();  
      #1 $display("[%0t] I am in process p1",$time);  
      $display("[%0t] Initial status check of p1: %s",$time,p1.status);  
      ->e1;  

      if(p1.status() != process :: FINISHED)  
         p1.kill();  
         $display("hi i am working");  
         $display("what about you?");  
   end:BEGIN_B2  

   begin:BEGIN_B3  
      wait(e1.triggered);  
      #1 $display("[%0t] Status of p1 before killing: %s",$time,p1.status());  
   end:BEGIN_B3  

join:FORK_F1  
```

In the above code snippet you can see that process p1 At #0 simulation time process class object was created.  
In the below Fig-6,  
* At #1 simulation time the status of p1 was **RUNNING**.  
* At #2 simulation time after using kill() method the status of p1 was **KILLED**.     

![fine_kill_output](https://user-images.githubusercontent.com/110447489/189288242-6fee6025-0dcb-4b17-a77c-55987ef9055a.png)

          Fig-6: The output of the kill() method.  

![fork join_any _self _kill-Page-3 drawio](https://user-images.githubusercontent.com/110447489/189514215-dbee3cbe-5d56-4ea6-ba0a-4339041efe8a.png)  

            Fig-7: scheduler Schematic for kill() method.



Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.sv

Github log_file link- https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.log 

## 4.await()  

This method is used to allows one process to wait for another process/Thread to complete.  

**Syntax**:-  
`Process p_handle1,p_handle2;`  
`initial begin`  
   `fork`  
      `begin`  
         `p_handle1 = process :: self();`  
         `p_handle2.await();`  
      `end`  
      `begin`  
         `p_handle2 = process :: self();`  
      `end`  
   `join`  
`end`  

**code snippet**:-  
```
$display("[%0t] Seeking status:",$time);  

fork:FORK_F1  

   begin:BEGIN_B2  
      p1 = process :: self();  
      #1 $display("[%0t] I am in process p1",$time);  
      $display("[%0t] Initial status of p1: %s",$time,p1.status());  
      $display("[%0t] Status of p1 before await: %s",$time,p1.status());  

      if(p1.status() != process :: FINISHED)  
         p2.await();  

   end:BEGIN_B2  

   #2 $display("[%0t] Status of p1 after await: %s",$time,p1.status());  

   begin:BEGIN_B4  
      p2 = process :: self();  
      #1 $display("[%0t] I am in process p2",$time);  
      $display("[%0t] Initial status of p2: %s",$time,p2.status());  
      #2 ->e2;  
   end:BEGIN_B4  

   begin:BEGIN_B5  
      wait(e2.triggered);  
      $display("[%0t] Final status of p2: %s",$time,p2.status());  
      ->e1;  
   end:BEGIN_B5  

   begin:BEGIN_B6  
      wait(e1.triggered);  
      $display("[%0t] Final status of p1: %s",$time,p1.status());  
   end:BEGIN_B6  
      
join_any:FORK_F1  
```

In the above code snippet we are trying to make process p1 to wait until the process p2 was finished.  
In below Fig-8, you can see  
* At #1 simulation time before using await() method the status of p1 was **RUNNING**.  
* At #2 simulation time after using await() method the status of p1 was **WAITING**.  
* At #3 simulation time once the status of p2 was **FINISHED** then the status of p1 also **FINISHED**.  

![fine_await_output](https://user-images.githubusercontent.com/110447489/189289551-413d96f1-1ea3-44be-b0ae-ecad906327c4.png)

          Fig-8: The output of the await() method.  

![await drawio](https://user-images.githubusercontent.com/110447489/189483050-8931484b-3aa1-4a65-bd8f-fbb3b967897a.png)  

               Fig-9: scheduler Schematic for await () method.



Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.log  

## 5.suspend()  

This method is used to suspend the execution of the process/Thread. It can suspend its own or other process’s execution. The execution is suspended until a resume() method is encountered.  
If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be suspended in the current timestamp.  

**Syntax**:-  
`Process p_handle1;`  
`initial begin`  
   `fork`  
      `begin`  
         `p_handle1 = process :: self();`  
         `p_handle1.suspend();`  
      `end`  
   `join_none`  
`end`  

**code snippet**:-  
```
$display("[%0t] Seeking status:",$time);  

   fork:FORK_F1  
      begin:BEGIN_B2  
         p1 = process :: self();  
         #1 $display("[%0t] I am in process p1",$time);  
         $display("[%0t] Initial status of p1: %s",$time,p1.status());  
         ->e1;  

         if(p1.status() != process :: FINISHED)  

         begin:BEGIN_B3  
            #1 $display("[%0t] Status of p1 before suspending: %s",$time,p1.status());  
            p1.suspend();  
            $display("[%0t] Status of p2 in p1 block: %s",$time,p2.status());  
         end:BEGIN_B3  
      
      end:BEGIN_B2  

      begin:BEGIN_B4  
         wait(e1.triggered);  
         p2 = process :: self();  
         #1 $display("[%0t] I am in process p2",$time);  
         $display("[%0t] Initial status of p2: %s",$time,p2.status());  
         #1 $display("[%0t] status of p1 after suspended: %s",$time,p1.status());  
         ->e2;  
      end:BEGIN_B4  

      begin:BEGIN_B5  
         wait(e2.triggered);    
         $display("[%0t] Final status of p2: %s",$time,p2.status());  
      end:BEGIN_B5  

join:FORK_F1  
```

In the above code snippet we are trying to make process p1 to suspend permanently.  
In the below Fig-10, you can see
* At #1 simulation time before suspending the status of p1 was **RUNNING**.
* At #3 simulation time after suspending the status of p1 was **SUSPENDED**.

![fine_suspend_output](https://user-images.githubusercontent.com/110411714/189474562-ae38bf97-2a1c-4b43-b9cf-19b4ae9d4908.png)

          Fig-10: The output of the suspend() method.
 
Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.sv

Github log_file link-  https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.log

          Fig-11: scheduler Schematic for suspend () method.  

## 6.resume()  

This method is used to restart the process that was suspended. Resuming a process that was suspended while being blocked (due to wait statement, delay or waiting for an event to trigger) shall reinitialize that process to the event expression or wait for the wait condition to be true or for the delay to expire.  

**Syntax**:-  
`Process p_handle1,p_handle2;`  
`initial begin`  
   `fork`  
      `begin`  
         `p_handle1 = process :: self();`  
         `p_handle1.suspend();`  
      `end`  
      `begin`  
         `p_handle2 = process :: self();`  
         `p_handle1.resume();`  
      `end`  
   `join_none`  
`end`  

**code snippet**:-  
```
$display("[%0t] Seeking status:",$time);  

   fork:FORK_F1  

      begin:BEGIN_B2  
         p1 = process :: self();  
         #1 $display("[%0t] I am in process p1",$time);  
         $display("[%0t] Initial status of p1: %s",$time,p1.status());  
         ->e1;  

         if(p1.status() != process :: FINISHED)  
        
         begin:BEGIN_B3  
           #1 $display("[%0t] Status of p1 before suspending: %s",$time,p1.status());  
           p1.suspend();  
           $display("[%0t] Status of p2 in p1 block: %s",$time,p2.status());  
         end:BEGIN_B3  

      end:BEGIN_B2  

      begin:BEGIN_B4  
         wait(e2.triggered);  
         $display("[%0t] Status of p1 before resuming: %s",$time,p1.status());  
         p1.resume();  
         #1 $display("[%0t] Status of p1 after resuming: %s",$time,p1.status());  
         ->e3;  
      end:BEGIN_B4  

      begin:BEGIN_B6  
         p2 = process :: self();  
         #1 $display("[%0t] I am in process p2",$time);  
         $display("[%0t] Initial status of p2: %s",$time,p2.status());  

         if(p1.status() == process :: SUSPENDED)  
            #1 ->e2;  
      end:BEGIN_B6  

      begin:BEGIN_B7  
         wait(e3.triggered);  
         #1 $display("[%0t] Final status of p1: %s",$time,p1.status());  
         $display("[%0t] Final status of p2: %s",$time,p2.status());  
      end:BEGIN_B7  

join:FORK_F1
```

Here in the above code snippet we are trying to resume the process p1 in the process p2.  
In the below Fig-12, you can see  
* At #1 simulation time the status of p1 was **RUNNING**.  
* At #2 simulation time before using resume() method the status of p1 was **SUSPENDED**.
* At #3 simulation time after using resume() method the status of p1 was **FINISHED**.  

![fine_resume_output](https://user-images.githubusercontent.com/110447489/189291418-e4c49026-c40b-49fe-9f35-6119a9bfa80e.png)

          Fig-12: The output of the resume() method.  

![resume drawio](https://user-images.githubusercontent.com/110447489/189482693-48130761-8a3f-4501-b997-bc4810791883.png)  

        Fig-13: scheduler Schematic for fork-join code.


Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.log
