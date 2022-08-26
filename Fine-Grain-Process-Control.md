# Fine Grain Process Control
SystemVerilog has a built in class named Process that allows one process(i.e, like fork_join) to access and control the processes/threads.
When we fork off any thread, a new object of process class is created at that time. This object contains status information about that thread.

![Untitled Diagram drawio (5)](https://user-images.githubusercontent.com/110509375/186867756-112267e1-547f-4882-8561-b04bcbd63805.png)

          Fig-1: These are all the methods which are available in fine grain process control.

## Cheat sheet Links
|      **Tasks**         |     **Description**  |
|:---------------------- | :--------------------|
|[self()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control#self)|     will return the handle of the process|
|[kill()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#kill)   |   will kill the thread     |
|[status()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#status)|will return information about which mode the current thread is|
|[await()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#await)| waits for some other thread to complete.|
|[suspend()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#suspend)| suspends the thread for some indefinite time|
|[resume()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#resume)| resumes the thread from suspended state|

## self()
It creates the object for process class. The object is used to access all the methods of process class.   

Here in the below Fig-2 you can see that at 0ns time the object was not created but after 10ns time we used self() method in the code so the object was created.

![self](https://user-images.githubusercontent.com/110447489/186918391-9abe783b-1538-4764-a5eb-5105ee94345f.jpg)

          Fig-2: The output of the self() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.log

## Status()
It will shows the status or state of the process i.e Finished,Running,Waiting,Suspended,Killed.  

Here in the below Fig-3 you can see that there are some strings which are in upper-case those are the status of a process p1 and p2.

![status](https://user-images.githubusercontent.com/110447489/186918464-d50a89cc-c8ae-4b16-97b6-00159fd7fbd0.jpg)

          Fig-3: The output of the status() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.sv  

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.log  

## kill()
The kill () function terminates the process and all its sub-processes. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be terminated in the current timestamp.

Here in the below Fig-4 we can see that process p1 is started and running at 4ns but at 5ns by using kill() method we killed the process p1.  

![kill](https://user-images.githubusercontent.com/110447489/186920953-8f5deced-828e-4944-8ee1-3c16734410bc.jpg)

          Fig-4: The output of the kill() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.sv

Github log_file link- https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.log 

## await()
This task allows one process to wait for another process.  

Here in the below Fig-5 we are trying to make process p1 to wait until the process p2 was finished. so you can see that at 7ns process p1 was waiting till 9ns for process p2 and at 11ns process p1 was finished.

![await](https://user-images.githubusercontent.com/110447489/186921010-49531f05-485a-4308-af15-a15d1c33c991.jpg)

          Fig-5: The output of the await() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.log  

## suspend()
This function suspends the execution of the process. It can suspend its own or other process’s execution. The execution is suspended until a resume () is encountered. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be suspended in the current timestamp.  

Here in the below Fig-6 we can see that process p1 at 7ns was suspended and we are not using resume() method so the process p1 was still in suspended state even at 11ns.

![suspend2](https://user-images.githubusercontent.com/110447489/186922121-b24067a5-fe97-4838-8ac7-3506578b49a5.jpg)

          Fig-6: The output of the suspend() method.
 
Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.sv

Github log_file link-  https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.log

## resume()  
This function restarts the process that was suspended. Resuming a process that was suspended while being blocked (due to wait statement, delay or waiting for an event to trigger) shall reinitialize that process to the event expression or wait for the wait condition to be true or for the delay to expire.  

Here in the below Fig-7 we can see at 7ns process p1 was suspended and at 16ns i was checking the status before using resume() method it was showing suspended so then at 17ns after using resume() method the status of process p1 is running and then it was finished.

![resume](https://user-images.githubusercontent.com/110447489/186921148-5ad587d6-c786-4bcd-aefe-d87fbe52f673.jpg)

          Fig-7: The output of the resume() method.

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.sv

Github log_file link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.log
