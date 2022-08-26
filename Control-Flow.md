
## Conditional Statement 
Conditional statement  are used for executing the statements by giving the conditions. These statements until the condition become false . 
There are various types of conditional statements - 
### if 
 This statement is use for giving a single condition and   inside it executing the multiple statements or single statement . This is generally use for comparison of a number or two numbers .

**Syntax**   
              `if(condition)begin  `  
               `statements;  `  
               `end`  

**log file link**  


***
### if else

This statement , first the compiler goes to the if condition and checks the condition and execute it if it is true  or if "if" condition is not true , the compiler will go to the "else" statement and checks the condition either it is true or not . If the "if" or "else" any one of them is not true , then the compiler show the error .

**Syntax** -     
               `if(condition)begin  `    
               `statements;  `   
               `end   `  
               `else begin    `  
               `Statements;  `  
               `end`  

**Lab link**




***

### if else ladder 

This statement is use by giving the multiple conditional statements . These statements are 'if elseif elseif .... else' . First the compiler checks the 'if 'condition and execute it if it is true  or if it is false, it will jump to the elseif condition and execute and soo on , at last it will come to else condition . 

**Syntax** -   
`              if(condition)begin  `  
              `Statements;  `  
              `end   `
              `elseif (condition)begin  `  
              `Statements;   `  
              `end  `
              `elseif(condition)begin  `  
              `Statements;  `  
              `end   `  
               `...  `  
               `...  `  
              `else begin  `  
              `Statements;  `  
              `end  `  

**lab link**  


***
There are three new conditional statements are introduced in system verilog . These are -

1. unique if 
2. unique0 if 
3. priority if 

***

### unique if
This statement is same as the if condition statement when only one condition is true in the whole code . 

If more than the conditions are true this statement execute the first one which is true ,gives the output and will not write any error only write the warning(that more than one statement is true).
If all the statements are false ,it will not display any error but will display a warning .

Below lab example will show how unique if is different from the traditional if else statement .

  **Syntax** -  
`               unique if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `elseif(condition)begin  `  
               `Statements;  `  
               `end  `  




**lab link**  


***
###  unique0 if 

This statement is same as the if condition statement when only one condition is true in the whole code . 

If more than one condition is true , it will read the first true condition and display the output without any error but display a warning (more than one condition is true ).
If more than one condition is false , it will not display any output , not even any error and warning.

Below examples will show the difference between the unique0 if and traditional if else condition .

  **Syntax** -    
`               unique0 if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `else if(condition)begin  `  
               `Statements;  `  
               `end  `  
  

**lab links**


***
###  priority if 

This is again a update version of if else condition statement .When only one condition is true , it will work same as the if else condition . 

When more than one condition is true , it will execute the first true condition and gives the output and it will not display any error not even warning.

When all the conditions are false it will display only a warning . 

Below example will properly show the working idea of the priority if condition .

**Syntax** -    
`               priority if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `else if(condition)begin  `  
               `Statements;  `  
               `end  `  
              
              
  
**lab link**


***




## class  
The case statement allows us to execute the code for the particular case expression . 
This will give the proper structure for a long code and decrease the complexity of the code also .  
There are three updates for the case statement in system verilog and these are -  
1. unique case  
2. unique0 case  
3. priority case  

***
### unique case 

In this , if all the case condition is false , it will display a warning (not match is found for the case statement )with no error .
If all the conditions are true or more than one is true , it will read the first right or matched case condition and will display the output with one warning and no error.

**Syntax**-  
`            unique case(condition)  `  
            `condition_1: Statements ;  `  
            `.......`  
            `conditon_N:  Statements ;  `  
            `endcase  `  

**lab link** 


***

### unique0 case 


     

***
### priority case 

In this type of case statement, if more than one case condition is true , it will display the output without giving any error with no warning .

**Syntax**-  
`             priority case (condition)  `  
             `case_1: statement;  `  
             `----  `  
             `case_N: statement ;  `  
             `endcase `  
   
**lab link** - 




***















## Loops 

The loops has a sequence of instructions , it will execute when the instruction is true and execute until the condition of loops will not false . When the condition become false , the loops will terminate . 
There are various kinds of loops  -
 
**Pictures of loops**


***



### 1. for 
for loop, execute the statements multiple times until the statement become false . Execution of "for loop" require three steps -

a. Initialization - It will firstly initialize the variable .
b. condition -  give condition to the loops . It will decide the purpose of the loop.
c. modifier - means in this part , the increment or decrement done .

**Syntax** -   
`              for (initialization; condition; modifier) begin  `    
              `Statements;  `    
              `end   `  ##   

**lab link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/for_loop/for_code.sv  

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/for_loop/for_loop_output.log  


*** 
### 2. foreach

This loop is the update version of for loop in system verilog . As compare to for loop , foreach loop syntax is less complicated .
When the condition is true , the statements of the loop execute until the condition become false same as for loop .

**Syntax** -    
`               foreach(variable[iterator])begin  `  
               `Statements;  `  
               `end   `  

Below example will give the working idea of foreach loop .

**lab link** -


**lab output link** -


***
 
### 3. forever loop
As the name says forever loop will execute the statements inside the loop forever.  
It can be said as indefinite iteration.

**Syntax** -   
`           forever begin  `  
           `multiple statements;  `  
           `end  `  
  
Below example gives the idea of the working of forever loop .

**lab link** -   
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/forever_loop/forever_code.sv      

**lab output link**    
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/forever_loop/forever_loop_output.log    



***

### 4. while

In this loop , first condition is checked , if it is true and the statements inside the while loop will execute until the condition become false .

**Syntax** -   
`               while(condition)begin              `  
               `Statements;  `  
               `end  `  
Below example will give the idea about the working of the while loop.

**lab link** -


***
 ### 5. do while 

This loop will execute the condition first and then checks the condition . Then if the condition is true , the statement inside the while loop will execute until the condition become false .

do while loop execute the statements atleast once if the condition is false .

**Syntax** -  
`                 do begin                 `  
                 `Statements;           `  
                 `end                  `  
                `while(condition)begin     `  
                `Statements;  `  
                `end  `  

**lab link** -


***

### 6. break 
 
Break is use to terminate the any loop . Generally, we use break after giving the condition in code using the if statement.

We can use break statement in any loop(for , while , do-while), for terminating the execution of loop . It is always use inside the loop.

**Syntax** - `break;`  

Below example will show ,how to terminate the loop using the break statement .

**lab link** -


***

### 7. continue 

This statement is generally use for skipping the statements in the loop . It is also use inside the loops .

**Syntax** - `continue;`   

Below example will show how the continue  statement work . 


***

### 8. repeat 

This loop is use for the repeating of statements or operation for fix number of times .

**Syntax** -  
             `repeat(no. of times)begin  `  
             `statements;  `  
             `end  `  

**lab link** - 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_code.sv  

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_loop_output.log  


***

## Blocking and non blocking statement - 
### Blocking statement  
Blocking statements are assigned with = . It will execute one after the other in procedural blocks . Blocking statements are execute in a block in a sequential manner but when more than two procedural blocks , these statements will execute parallelly in the blocks and will not block the statements of other procedural blocks .

**Syntax** -  
`            variable_datatype variable name = value assign;`  

For example - 1. Time delay assignation 

  
` module blocking_assignment;  `  
`int a , b;`  
`initial begin `  
`#10 a = 10;`  
`#20 b = 20;`  
`end `  
`endmodule `  

 In this code , there are two variables a and b . The value assign to a = 10 after the 10sec and the value assign to b = 20 after the time delay of 20+10=30 sec . 


Example 2 - Swapping of two number using blocking statement .  
**Code**  
`module non_blocking;`  
`login [4:0] a , b;`  
`initial begin `  
`a=10;`  
`b=30;`  
`int t;  // introducing the temporary variable.  `  
`// swapping two number using the temporary variable //`  
`a=t;  // t=10;`  
`t = b;  // b=10;`  
`b= a ;  // a = 30;`  
`$monitor(" a = %d , b= %d", a,b);  `  
`end `  
`endmodule `  

**Output**  
a=30 , b = 10

**lab links**


***

### Non - blocking statement  

 Non - blocking statement are assign with the <=. It will not block the execution of statement inside that particular block.
These statement will execute the parallel inside that particular block . 

**Syntax** -  
`             data_type_name variable_name <= value assignation ;`  
 
For example-1-  
**Code**  
` module blocking_assignment;  `  
`int a , b;`  
`initial begin `  
`#10 a <= 10;`  
`#20 b <= 20;`  
`end `  
`endmodule `  

 In this code , there are two variables a and b . The value assign to a = 10 after the 10sec and  parallel the value assign to b = 20 after the time delay of 20 sec . 
             

Example2 -  Swapping of two numbers 
**Code**  
`module non_blocking;  `  
`logic [4:0] a ,b;  `  
`initial begin  `  
`a= 20;`  // assigning the values to a and b   
`b= 30;`  
`a<=b;  `// Assign the value to b to a    
`b<=a;  `  // Assign the value of b to a   
`$monitor("The value of a and b after swapping is %d %d" , a, b );  `    
 `end   `  
`endmodule   `    

**Output**  
The value of a and b after swapping is 30 and 20 .

**lab link**













***


## Function and task 

S.No.|Function | Task |
:-----|:--------|:------|
1.|Not have timing control statents| have timing control statements|
2.|  Can return some value | Cannot return any value|
3.| Can call only other functions , not tasks .|Can call other task and function both.|
4.| only return input arguments | Can return input , output and inout arguments |




***

### Function 

The function is the subroutine that contain procedural code.
The purpose of the function is to return the value that can be used in the expression .
The function cannot have time control statements like # , @ or fork join( The function must execute in zero time .)  
A function can call other functions not other tasks .
A function can have atleast one argument but not have any inout or out argument .


**Syntax** -  
  `function data_type function_name(arguments )`  
`    <Statements>;  `  
    `endfunction  `  

Arguments are of two types - 
1. formal argument - declare in the routine header.

2. actual argument - value and function passed to and from the routine.

We can call the function mainly by two ways -
1. call by value   
2. call by reference  

### call by value 

In argument pass by value, the argument passing mechanism works by copying each argument into the subroutine area.

If any changes to arguments within the subroutine, those changes will not be visible outside the subroutine.

Below example will show the clear overview of working of call by value function .

**lab link**


***

### call by reference 

In this , the reference to the original argument is passes to the subroutine .As the argument within a subroutine is pointing to an original argument, any changes to the argument within subroutine will be visible outside.

Below example will show the clear idea .

**lab link**

 


***

 ## task 

The task is use to split the code in into small parts same as function but there are some differences in between them .  
In task , we can provide time delays like # , @ .etc.  
Task can call other tasks and functions also .
Task cannot return anu value .
We can assign input ,output and inout argument in task , which is not possible in functions.
 
**Syntax** -  
`task task_name(arguments)`  
`Statements;  `  
`endtask  `  

There are generally two type to task we use -  
1. Static task   
2. Automatic task  


***

### Static task 

Static tasks share the same storage space for all task calls.

**lab link** -


***

### Automatic task 

Automatic tasks allocate unique, stacked storage for each task call.


***
## events 

Event is use for synchronizing between two or more concurrently active processes. First process will trigger the event another one is wait for the event .  
Event can trigger by using the -> or ->> operator .
Processes can wait for event by using the @ operator or .triggered .






 



             
