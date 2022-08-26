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
## Status()
It will shows the status or state of the thread i.e Finished,Running,Waiting,Suspended,Killed.
## 
