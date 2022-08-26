# Fine Grain Process Control
SystemVerilog has a built in class named Process that allows one process(i.e, like fork_join) to access and control the processes/threads.
When we fork off any thread, a new object of process class is created at that time. This object contains status information about that thread.

![Untitled Diagram drawio (5)](https://user-images.githubusercontent.com/110509375/186867756-112267e1-547f-4882-8561-b04bcbd63805.png)

## Cheat sheet Links
|      **Tasks**         |     **Description**  |
|:---------------------- | :--------------------|
|[self()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control#self)|     will return the handle of the process|
|    kill()   |   will kill the thread     |
|[status()](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Fine-Grain-Process-Control/#status)|will return information about which mode the current thread is|
|await()| waits for some other thread to complete.|
|suspend()| suspends the thread for some indefinite time|
|resume()| resumes the thread from suspended state|
## self()
It creates the object. To access others we need to create  object first.  

![self](https://user-images.githubusercontent.com/110447489/186918391-9abe783b-1538-4764-a5eb-5105ee94345f.jpg)


Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.sv  

Github output link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_self/fine_self.log
## Status()
It will shows the status or state of the thread i.e Finished,Running,Waiting,Suspended,Killed.  

![status](https://user-images.githubusercontent.com/110447489/186918464-d50a89cc-c8ae-4b16-97b6-00159fd7fbd0.jpg)


Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.sv  

Github output link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_status/fine_status.log  

## kill()
The kill () function terminates the process and all its sub-processes. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be terminated in the current timestamp.  

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.sv

Github output link- https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_kill/fine_kill.log 
## await()
This task allows one process to wait for another process.  

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.sv

Github output link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_await/fine_await.log  

## suspend
This function suspends the execution of the process. It can suspend its own or other process’s execution. The execution is suspended until a resume () is encountered. If the process is not blocked (due to wait statement, delay or waiting for an event to trigger), then it will be suspended in the current timestamp.  
 
Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.sv

Github output link-  https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_suspend/fine_suspend.log
## resume()  
This function restarts the process that was suspended. Resuming a process that was suspended while being blocked (due to wait statement, delay or waiting for an event to trigger) shall reinitialize that process to the event expression or wait for the wait condition to be true or for the delay to expire.  

Github lab link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.sv

Github output link-https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_BJT/fine_grain_process_control/fine_resume/fine_resume.log
