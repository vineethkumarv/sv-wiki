

In Verilog, the communication between blocks is specified using module ports.

****Disadvantage of verilog module connections****

* Declaration must be duplicated in multiple modules.  
* Risk of mismatched declaration.  
* A change in design specifications can require modifications in multiple modules.

# Interface

 SystemVerilog adds the ****interface**** construct which encapsulates the communication between blocks. An ****interface**** is a bundle of signals or nets through which a testbench communicates with a design. 

sl. no. | **data type**         |
|:--|:---------------------- |
|1.|[Interface]() |
|2.|[Parameterized interface]() |
|3.|[Modports]() | 
|4.|[Clocking blocks]() |
|5.|[Virtual interface]() |


        Tabular column.1. Interface  

![interface1](https://user-images.githubusercontent.com/110443214/188564362-e80552d8-68ba-474a-a552-678f2a647c26.JPG)
   
                                            Figure.1.Interface types

The interface construct is used to connect the design and testbench.

systemverilog without Interface 

Below diagram shows connecting design and testbench without interface.

![int Diagram](https://user-images.githubusercontent.com/110443214/187849761-4804babe-bebe-4c8f-8c41-b08bf7dd3e0d.jpg)

                        Figure.2.top module without interface
 
 


SystemVerilog Interface

Below diagram shows connecting design and testbench with the interface.

![interface Diagram](https://user-images.githubusercontent.com/110443214/187851196-6acc7850-4fb0-4960-9515-3a329d724e28.jpg)
 
                        Figure.3.top module without interface


---

****Syntax****:


`interface (interface_name) ([port_list]);`  
 ` [list_os_signals] `    
`endinterface`  


****Example****:
**Interface declaration**

`interface and_if;`   
`logic input_a,input_b,output_y;`       
`endinterface`    


**TOP module for AND gate**

    //Here the interface,testbench,design module are called.
    module top();
    
    //interface module
    and_if inf();
    
    //design module instantiate
    andg a1(.input_a(inf.input_a), .input_b(inf.input_b), .output_y(inf.output_y));
    
    //testbench
    tb a2(inf);
    
    endmodule:top

    
  

Below figure shows the output of **and** **gate** using interface.

![interface 1png](https://user-images.githubusercontent.com/110443214/188553269-4f18c2b3-0670-4e98-b4a2-a0f86ace3ba5.png)

                                         Figure.4.output for and gate with interface

****Advantages of SystemVerilog interfaces****


* In Verilog for the addition of new signals, it has to be manually changed everywhere that module has been instantiated. System Verilog made it easier to add new signals in the interface block for existing connections.
* It has increased re-usability across the projects.
* A set of signals can be easily shared across the components bypassing its handle.
* It provides directional information (modports) and timing information (clocking blocks).
* Interfaces can contain parameters, variables, functional coverage, assertions, tasks and functions.
* Interfaces can contain procedural initial and always blocks and continuous assign statements.

---


## Parameterized interface  

Parameters can be used in interfaces to make vector sizes and other declarations within the interface reconfigurable using Verilog’s parameter redefinition constructs.


****Syntax****

`interface (interface_name) #(parameter parameter_name = initialize);`  
 ` [list_os_signals] `    
`endinterface` 


****Example****

`interface count_if #(parameter N=2) ;`  
`logic reset,clk;`  
`logic [N:0] counter;`  
`endinterface`  


**TOP module for COUNTER**

    //Here the interface,testbench,design module are called.
     module top();
   
    //parameterised interface
     count_if inf();
  
    //design code of up_counter
    up_counter u1(.clk(inf.clk), .reset(inf.reset), .counter(inf.counter));
 
    //testbench for up_counter
    upcounter_testbench u2(inf);
 
    endmodule:top

Here we're considering 3 bit output, where the counter counts from 0 to 7.  

Below figure shows the output of counter with parameterized interface.

![para_interf1](https://user-images.githubusercontent.com/110443214/188553684-3e4dd712-73ba-4bb8-90fd-c0e64b6b1a65.png)

                                  Figure.5.Output for counter with parameterized interface




In Verilog, the communication between blocks is specified using module ports.

****Disadvantage of verilog module connections****

* Declaration must be duplicated in multiple modules.  
* Risk of mismatched declaration.  
* A change in design specifications can require modifications in multiple modules.

# Interface

 SystemVerilog adds the ****interface**** construct which encapsulates the communication between blocks. An ****interface**** is a bundle of signals or nets through which a testbench communicates with a design. 

sl. no. | **data type**         |
|:--|:---------------------- |
|1.|[Interface]() |
|2.|[Parameterized interface]() |
|3.|[Modports]() | 
|4.|[Clocking blocks]() |
|5.|[Virtual interface]() |


        Tabular column.1. Interface  

![interface1](https://user-images.githubusercontent.com/110443214/188564362-e80552d8-68ba-474a-a552-678f2a647c26.JPG)
   
                                            Figure.1.Interface types

The interface construct is used to connect the design and testbench.

systemverilog without Interface 

Below diagram shows connecting design and testbench without interface.

![int Diagram](https://user-images.githubusercontent.com/110443214/187849761-4804babe-bebe-4c8f-8c41-b08bf7dd3e0d.jpg)

                        Figure.2.top module without interface
 
 


SystemVerilog Interface

Below diagram shows connecting design and testbench with the interface.

![interface Diagram](https://user-images.githubusercontent.com/110443214/187851196-6acc7850-4fb0-4960-9515-3a329d724e28.jpg)
 
                        Figure.3.top module with interface


---

****Syntax****:


`interface (interface_name) ([port_list]);`  
 ` [list_os_signals] `    
`endinterface`  


****Example****:

`interface and_if;`   
`logic input_a,input_b,output_y;`       
`endinterface`    

Below figure shows the output of **and** **gate** using interface.

![interface 1png](https://user-images.githubusercontent.com/110443214/188553269-4f18c2b3-0670-4e98-b4a2-a0f86ace3ba5.png)

                                         Figure.4.output for AND gate with interface

****Advantages of SystemVerilog interfaces****


* In Verilog for the addition of new signals, it has to be manually changed everywhere that module has been instantiated. System Verilog made it easier to add new signals in the interface block for existing connections.
* It has increased re-usability across the projects.
* A set of signals can be easily shared across the components bypassing its handle.
* It provides directional information (modports) and timing information (clocking blocks).
* Interfaces can contain parameters, variables, functional coverage, assertions, tasks and functions.
* Interfaces can contain procedural initial and always blocks and continuous assign statements.

---


## Parameterized interface  

Parameters can be used in interfaces to make vector sizes and other declarations within the interface reconfigurable using Verilog’s parameter redefinition constructs.


****Syntax****

`interface (interface_name) #(parameter parameter_name = initialize);`  
 ` [list_os_signals] `    
`endinterface` 


****Example****

`interface count_if #(parameter N=2) ;`  
`logic reset,clk;`  
`logic [N:0] counter;`  
`endinterface`  

Here we're considering 3 bit output, where the counter counts from 0 to 7.  

Below figure shows the output of counter with parameterized interface.

![para_interf1](https://user-images.githubusercontent.com/110443214/188553684-3e4dd712-73ba-4bb8-90fd-c0e64b6b1a65.png)

                                  Figure.5.Output for counter with parameterized interface


