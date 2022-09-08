

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


# Virtual Interface
* The virtual interface is a variable that represent the interface instance.
* The virtual interface is used to create a interface instance in the class because the interface is a static component and the system verilog test bench is a dynamic component. we cannot directly declare the interface in the class by using the variable **virtual** we can declare the interface instance in the class

   `synatax: virtual interface_name instance_name;`

interface_name: name of the interface  
instance_name: name of the interface instance can be called in the class with variables Ex: vif.variable;  
* The virtual interface must be initialized in the class pointing to actual interface.
    Declaration of virtual interface in the class
    `Example: Virtual intf vif;  

* Accessing of uninitialized virtual interface result in fatal error.

* The virtual interface can be passed as argument to the task and function methods.    

* The virtual interface can be a property of class and which is  initialized by using the function argument i.e it can call the actual interface in the particular class and create the instance of interface in that class

     `Example: function new(virtual intf vif);`  

* The virtual interface can be passed as argument to the function methods
Calling the actual interface 'intf'  to declare the virtual interface in the class using the procedure or in function argument by using  new() construct. 

*  The interface variables can be accessed by  virtual interface handles inside the class function and task methods as **virtual_instance_name.variable**;  

`Example : vif.a`  

 vif is a virtual_instance_name;  
 a is the variable/property of class  

* The keyword/signal virtual interface variable represent the different interface instance in different time through out the simulation time


  **syntax:** 
`interface <interface_name>();  `
               `<port_list>;  `
                `..........  `
                `endmodule  `
           `To connect static(interface module) to   `
           `to dynamic(class) we use virtual interface  `
            `class clase_name;`
             `virtual <interface_name> <interface_instance>;`
             `.......`
           `properties;`
             `.....`
           `function()`
            `.....`
          `endfunction    `
            `task();`
             `......`
             `endtask`
             `endclass`

Example1: Fulladder 

  **Interface module of full adder**

    `interface adder();
     logic in_a,in_b,in_c;
      logic out_sum,out_carry;
     endinterface

**Virtual Interface declaration inside the class**

      `//class:driver.sv
        class driver;
 
       //Declaration of virtual interface
       //syntax: virtual interface_name interface_instance;
       virtual adder vif;
 
       //constructor
       function new(virtual adder vif);
        //this.vif refer to class driver
       //vif refer to the function argument
       this.vif = vif;
 
     endfunction
    //task
     task run();
 
       repeat(10) begin
      //interface_instance.variable
      vif.in_a = $random;
      vif.in_b = $random;
       vif.in_c = $random;
       $display("");
       $display("//INPUT:Values  \n a=%0b, b=%0b, cin =%0b", vif.in_a,vif.in_b, vif.in_c);
        #5;
       $display("");
      $display("//OUTPUT: \n sum=%0b, carry = %0b\n", vif.out_sum, vif.out_carry);
 
    end
   endtask
 endclass
 

**Top module of full adder**

      //including the test.sv and interface.sv files
    `include "test.sv"
    `include "interface.sv"
 
     //module:top
     module top;
    //creating  an instance of interface
     adder intf();
 
    // the instance of test  t1.
     test t1(intf);
 
    //fulladder DUT instance , connecting the interface signal to instance DUT
    fulladder dut(.in_a(intf.in_a), .in_b(intf.in_b), .in_c(intf.in_c), .out_sum    (intf.out_sum), .out_carry(intf.out_carry));
    endmodule
 


**Below figure shows the design block of the code:**

![Untitled Diagram (9)](https://user-images.githubusercontent.com/110412474/189041289-6b5d0e96-1d6b-4478-b39e-f61a12b3fbea.jpg)
 
                                     Fig.1: Design Block diagram

Here in the Figure:1, the driver is a class here we declare the virtual interface because inside the class we cannot call the interface directly because interface is static component and class is dynamic component. so this virtual keyword is used to create the instance in the class (it will create the memory space) inside the class. In driver we generates the random stimulus and send to the interface, the DUT signals are connected to interface. The DUT output is given to the interface the test block consist of class and the top module consist of all the component such as test, interface and DUT the instance of all component is created in the Top module/block.



**Below figure shows the output of full adder:**  
Here in the Figure.2 shows the output of full adder where a, b & cin are the input of the full adder, sum and carry are the output of the fulladder

![fulladder output](https://user-images.githubusercontent.com/110412474/189043253-50ccf9fc-da80-4534-b14e-c01dce833a4f.JPG)

                                    Fig: Output of Full adder 



