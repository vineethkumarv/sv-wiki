# Fine Grain Process Control

System Verilog has a built in class named Process that allows one process(i.e, like fork_join) to access and control the processes/threads. When we fork off any thread, a new object of process class is created at that time. This object contains status information about that thread.  

![Untitled Diagram drawio (5)](https://user-images.githubusercontent.com/110509375/186867756-112267e1-547f-4882-8561-b04bcbd63805.png)

          Fig-1: These are all the methods which are available in fine grain process control.

## Cheat sheet of different fine-grain process control:

|      **Tasks**         |     **Description**  |
|:---------------------- | :--------------------|
|[self()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control#self)|     will return the handle of the process|
|[kill()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#kill)   |   will kill the thread     |
|[status()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#status)|will return information about which mode the current thread is|
|[await()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#await)| waits for some other thread to complete.|
|[suspend()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#suspend)| suspends the thread for some indefinite time|
|[resume()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#resume)| resumes the thread from suspended state|

## 1.self()
It creates the object/ID for process class. The object is used to access all the methods of the process class.  

**code snippet**  
```
fork:FORK_F1  

   $display("[%0t] Entered into fork-join and started first check for the process",$time);  
   #1 ->e1;  

   begin:BEGIN_B2  
      wait(e1.triggered);  
      if(p1 == null)  
         #1 $display("[%0t] Not created",$time);  
      else  
         #1 $display("[%0t] Created",$time);  
      ->e3;  
      ->e2;  
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

In the below Fig-2 you can see that At #0 time the object for the process was not created which is shown At #3 but after 10ns time we used self() method in the code so the object was created.

![snap self](https://user-images.githubusercontent.com/110447489/188852816-d3a77ddf-15c6-416c-ba7c-34e0b28dde05.jpg)


          Fig-2: The output of the self() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.log

## Status()
It will shows the status or state of the process i.e Finished,Running,Waiting,Suspended,Killed.  

**code snippet**  

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

Here in the below Fig-3 you can see that there are some strings which are in upper-case those are the status of a process p1 and p2.

![snap status](https://user-images.githubusercontent.com/110447489/188853934-e79b1b4a-0726-4636-a982-a8ecf5e7cdf5.jpg)


          Fig-3: The output of the status() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.log  

## kill()
The kill () function terminates the process and all its sub-processes. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be terminated in the current timestamp.  

**code snippet**  

     $display("[%0t] Seeking status:",$time);

      fork:FORK_F1

        begin:BEGIN_B2
         p1 = process :: self();
         #1 $display("[%0t] I am in process p1",$time);
         $display("[%0t] Initial status check of p1: %s",$time,p1.status); 
         ->e1;
        
         if(p1.status() != process :: FINISHED)
           p1.kill();
        end:BEGIN_B2
      
       begin
         wait(e1.triggered);
         #1 $display("[%0t] Status of p1 before killing: %s",$time,p1.status());
       end

      join:FORK_F1


Here in the below Fig-4 we can see that process p1 is started and running at 4ns but at 5ns by using kill() method we killed the process p1.  

![snap kill](https://user-images.githubusercontent.com/110447489/188854422-e29291ce-76cd-4153-a241-b100ecebbf54.jpg)


          Fig-4: The output of the kill() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.sv

Github log_file link- https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.log 

## await()
This task allows one process to wait for another process.  

**code snippet**  

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

Here in the below Fig-5 we are trying to make process p1 to wait until the process p2 was finished. so you can see that at 7ns process p1 was waiting till 9ns for process p2 and at 11ns process p1 was finished.  

![snap await](https://user-images.githubusercontent.com/110447489/188854896-70bd06a5-a9e2-4869-a0d0-326bf1593eac.jpg)


          Fig-5: The output of the await() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.log  

## suspend()
This function suspends the execution of the process. It can suspend its own or other process’s execution. The execution is suspended until a resume () is encountered. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be suspended in the current timestamp.  
**code snippet**  

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
          ->e2;
         end:BEGIN_B4

         begin:BEGIN_B5
          wait(e2.triggered);
          #1 $display("[%0t] Final status of p1: %s",$time,p1.status());
          $display("[%0t] Final status of p2: %s",$time,p2.status());
         end:BEGIN_B5

       join:FORK_F1


Here in the below Fig-6 we can see that process p1 at 7ns was suspended and we are not using resume() method so the process p1 was still in suspended state even at 11ns.

![snap suspend](https://user-images.githubusercontent.com/110447489/188855408-809402de-8ed4-44fe-a5df-0f84d1360673.jpg)

          Fig-6: The output of the suspend() method.
 
Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.sv

Github log_file link-  https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.log

## resume()  
This function restarts the process that was suspended. Resuming a process that was suspended while being blocked (due to wait statement, delay or waiting for an event to trigger) shall reinitialize that process to the event expression or wait for the wait condition to be true or for the delay to expire.  

**code snippet**  

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
         ->e2;
       end:BEGIN_B4

       begin:BEGIN_B5
         wait(e2.triggered);
         #1 $display("[%0t] Final status of p1: %s",$time,p1.status());
         $display("[%0t] Final status of p2: %s",$time,p2.status());
       end:BEGIN_B5

      join:FORK_F1

     end:BEGIN_B1  

Here in the below Fig-7 we can see at 7ns process p1 was suspended and at 16ns i was checking the status before using resume() method it was showing suspended so then at 17ns after using resume() method the status of process p1 is running and then it was finished.

![snap resume](https://user-images.githubusercontent.com/110447489/188856168-9389e0ce-7b26-4b66-ab8e-97b6c0fc4c60.jpg)


          Fig-7: The output of the resume() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.log
