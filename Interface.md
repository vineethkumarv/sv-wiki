

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
|5.|[Virtual interface]()  |


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

****Github lab code link****: https://github.com/muneeb-mbytes/SystemVerilog_Course/tree/b7_team_kachori/interface/interface_example


****Github lab output link****: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/interface/interface_example/interface.log


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

****Github lab code link****: https://github.com/muneeb-mbytes/SystemVerilog_Course/tree/b7_team_kachori/interface/parameter_interface

****Github lab output link****: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/interface/parameter_interface/code.log

---

# Modport:

- Modport is used to groups and specifies the port directions to the wires/signals declared within the interface. modports are declared inside the interface with the keyword modport. 
- modport is an abbreviation for module port.

**Characteristics of modports:**

* It can have, input, inout, output, and ref.
* By specifying the port directions, modport provides access restrictions for signals.
* The Interface can have any number of modports, the wire declared in the interface can be grouped in many modports.
* We can't assign or drive the value of wire which is declared as modport input. it will give compilation error.

**Syntax:**

`interface <interface_name>;`    
 `// signals declaration`  
 `....`  
 `modport modport_name(input signal_name,output signal_name);`  
`endinterface`     

**Example:**

`interface and_intr;`    
  `logic input_p,input_q;`  
  `logic output_r;`  
  `modport design_andg(input input_p,input input_q,output output_r);`   
  `modport tb_andg(output input_p,output input_q,input output_r);`  
`endinterface : and_intr`  

**Note:-**  There are two ways to specifying the modport name in the design.

1. specifying the modport name in testbench and design file.
2. specifying the modport name in top module file.

**1.Top module for AND gate while calling modport name in testbench and design file:**

     // creating top module 
     // in this file design,testbench,interface modules are called
     module top();
     // interfce module called
     and_intr inf();
     // design module called
     and_gate a1(inf);
     // testbench module called   
     tb a2(inf);
     endmodule : top

**design file for AND gate:**

     // and gate design file  
     // module defination for and gate with interface instanciation  
     module and_gate(and_intr.design_andg inf);
     // assign the output using continuous assignment
       assign inf.output_r = (inf.input_p) & (inf.input_q); 
     endmodule : and_gate   

**testbench file for AND gate:**

    // testbench file for and gate design
    // module defination for testbench with interface instanciation
    module tb(and_intr.tb_andg inf);

     initial begin
       $display("// and gate output using modports\n");
       $monitor("input_p=%0b\t input_q=%b\t output_r=%b",inf.input_p,inf.input_q,inf.output_r);
       inf.input_p = 0; inf.input_q = 0; 
       #1;
       inf.input_p = 1; inf.input_q = 0; 
       #1;
       inf.input_p = 0; inf.input_q = 1;     
       #1;
       inf.input_p = 1; inf.input_q = 1; 
     end
    endmodule : tb


**2. Top module for AND gate while calling modport name in Top module file:**

     // creating top module 
     // in this file design,testbench,interface modules are called
     module top();
     // interfce module called
     and_intr inf();
     // design module called
     and_gate a1(inf.design_andg);
     // testbench module called   
     tb a2(inf.tb_andg);
     endmodule : top

**design file for AND gate:**

     // and gate design file  
     // module defination for and gate with interface instanciation  
     module and_gate(and_intr inf);
     // assign the output using continuous assignment
       assign inf.output_r = (inf.input_p) & (inf.input_q); 
     endmodule : and_gate   

**testbench file for AND gate:**

    // testbench file for and gate design
    // module defination for testbench with interface instanciation
    module tb(and_intr inf);

     initial begin
       $display("// and gate output using modports\n");
       $monitor("input_p=%0b\t input_q=%b\t output_r=%b",inf.input_p,inf.input_q,inf.output_r);
       inf.input_p = 0; inf.input_q = 0; 
       #1;
       inf.input_p = 1; inf.input_q = 0; 
       #1;
       inf.input_p = 0; inf.input_q = 1;     
       #1;
       inf.input_p = 1; inf.input_q = 1; 
     end
    endmodule : tb


Output of AND gate using modports in interface remains same for both of the above mentioned ways. it showing in below figure.

![modport_andgate](https://user-images.githubusercontent.com/110448056/189105843-cc4578b3-8544-4062-af44-990ee2745450.png)

                               Figure.1 AND gate Output

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/tree/b7_team_kachori/interface/modports

**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/interface/modports/modport.log

---
# Clocking Block  

The clocking block is defined that the mechanism to  synchronize sampling and driving of input and output signal with respect to clock event. It is  quite useful to use clocking blocks inside a testbench to avoid race condition in simulation. We can make  timing  explicitly when signals are synchronous to a particular clock. Clocking block can only declared inside a module ,interface. Clocking block only deals with  how the inputs and outputs are sampled and synchronized. Assigning  a value to a variable is done by  module, interface not the clocking block.  
 
## **Clocking block terminologies**  

**1. Clocking event**    

`clocking  clockingblock_name  @(posedge clk);` 

The event specification used to synchronize the clocking block, @(posedge clk) is the clocking event.

**2. Clocking signal**  

`input  from_Dut;`  
`output to_Dut;`  

Signals sampled and driven by the clocking block, from_DUT and to_DUT are the clocking signals,  

**3. Clocking skew**  

Clocking skew specifies  with respect to at which input and output clocking signals are to be sampled or driven respectively. A skew must be a constant expression and can be specified as a parameter.   

**Input and Output skews**   
   
`default input #1step output #0;`    

The default input skew and output skew is declared  like this,  `default input #1step output #0;` .Here default input skew takes #1step delay for getting the stable input for sampling process. After getting the stable output only the sampling the inputs to be done. The output skew takes only #0 delay means that we get the stable output at the current time slot itself.     

The below  figure shows that default input and output skew 

![image](https://user-images.githubusercontent.com/110484152/188798547-897dab18-5cd5-423c-b94d-048be1dc1b92.png)   

                                        Fig 1: default input #1step output #0  

The below figure shows the Input skew and output skew    

![image](https://user-images.githubusercontent.com/110484152/188549973-1030d92b-3525-460f-a83a-eb51cc694689.png)  

                                         Fig 2: Input skew and output skew    

Input  signals are sampling with respect to the clock event. If an input skew is specified then the signal is sampled at skew time units before the clock event. Then the  output signals are driving skew simulation time units after the corresponding clock event. Input  skew is implicitly negative because it happens before the clock.   

In Input skew, `#1step` sampled at the end of previous step ie, postponed region. `#0` sampled at the same time as their corresponding clock event ie, Observed Region.  

In Output skew is positive because it refers the time after the clock event. The input `#1step` will get stable input for previous slots and output `#0` driven at stable point in the current time slot.    


**Syntax**    

`clocking cb @(posedge clk);`  
`default input #1step output #0;`  
`input  from_Dut;`  
`output to_Dut;`  
`endclocking`    

**Timing Regions**    

* Race conditions are caused by mixing design and testbench events during the same time slot.
* System verilog introduces division of time slots.  

1.  Active Region: Simulation of design code in modules.    
2.  Observed Region: Assertions evaluated their design executes.    
3.  Reactive Region: Execution of testbench.    
4.  Postpone Region: Sampling signals after all design activity.   

The below figure shows that timing regions of Interface in  systemVerilog.  

![image](https://user-images.githubusercontent.com/110484152/188817365-8bd23adb-d71c-4050-81db-29ab1416b69a.png)  

                                              Fig 3: Timing Regions of Interface in systemVerilog  

Note: You can refer the SystemVerilog scheduling semantic for your reference (Topic: Processes) to know more about the execution regions.


**Example**  

`clocking cb @(posedge clk);`  
`default input #1 output #2;`  
`input  ;`  
`output ;`  
`endclocking`  

**Output**      
  


**Advantages of Clocking Block**
  
* Clocking block provides  race free condition between testbench and DUT.         
* Clocking block can be declared inside interface, module.     
* Clocking block helps the user to write testbenches with higher level of abstraction.   
* Simulation is more faster.   
* Separating clocking activities of design from its data assignments activities.    
* Save amount of code and and time in design execution.  
* There is one clock per clocking block    






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
    fulladder dut(.in_a(intf.in_a), .in_b(intf.in_b), .in_c(intf.in_c), .out_sum(intf.out_sum), .out_carry(intf.out_carry));
    endmodule
 


**Below figure shows the design block of the code:**

![fulladder](https://user-images.githubusercontent.com/110412474/189057965-1d4bdfbf-9bdc-4d18-b843-e10d7a2fb26f.jpg)

 
                                     Fig.1: Design Block diagram

Here in the Figure:1, the driver is a class here we declare the virtual interface because inside the class we cannot call the interface directly because interface is static component and class is dynamic component. so this virtual keyword is used to create the instance in the class (it will create the memory space) inside the class. In driver we generates the random stimulus and send to the interface, the DUT signals are declared in the interface. The DUT output is given to the interface. The test block consist of class component i.e (driver.sv)  and the top module consist of all the component such as test, interface and DUT. The instance of all component is created in the Top module/block.



**Below figure shows the output of full adder:**  
Here in the Figure.2 shows the output of full adder where a, b & cin are the input of the full adder, sum and carry are the output of the fulladder

![fulladder2](https://user-images.githubusercontent.com/110412474/189060495-1def6aff-2ef9-4597-83e5-47db63e09aa8.jpg)


                                    Fig: Output of Full adder 

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/tree/b7_team_kachori/interface/Virtual_interface

**Github output code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/interface/Virtual_interface/top.log


