   ![Untitled Diagram-Page-2 drawio (2)](https://user-images.githubusercontent.com/110447788/186902152-dc7802fb-763d-4cb9-a2aa-d5a70f2ba067.png)  

                             Figure.1. Control Flow

## Conditional Statement 
Conditional statements are used for executing the statements by giving the conditions. These statements will work according to the condition. 
There are various types of conditional statements - 

![Untitled Diagram-Page-1 drawio (3)](https://user-images.githubusercontent.com/110447788/187055885-99715bb3-e2ed-4a5e-aa69-57c8f0a003fd.png)


                             Figure.2. Conditional Statements

### if 
 This statement is used for giving a single condition and inside it executing the multiple statements or single statement. This is generally used for comparison of a number or two numbers.

**Syntax**   
              `if(condition)begin  `  
               `statements;  `  
               `end`  

**log file link** 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if/if_code.sv   

**lab output link**   
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if/if_code_output.log  



***
### if else

In this statement first, the compiler goes to the if condition and checks the condition and executes it if it is true or if the "if" condition is not true, the compiler will go to the "else" statement and checks the condition either it is true or not. If the "if" or "else" of any one of them is not true, then the compiler shows the error.

**Syntax** -     
               `if(condition)begin  `    
               `statements;  `   
               `end   `  
               `else begin    `    
               `Statements;  `  
               `end`  

**Lab link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if_else/if_else_code.sv  

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if_else/if_else_code_output.log  




***

### if else ladder 

This statement is used by giving multiple conditional statements. These statements are 'if elseif elseif .... else' . First, the compiler checks the 'if 'condition and executes it if it is true or if it is false, it will jump to the else if condition and execute, and so on, at last, it will come to the else condition. 

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
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if_else_ladder/if_else_ladder_code.sv  

**lab output link** 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/if_else_ladder/if_else_ladder_output.log  


***
There are three new conditional statements are introduced in the system Verilog. These are -

1. unique if 
2. unique0 if 
3. priority if 

***

### unique if
This statement is the same as the if condition statement when only one condition is true in the whole code. 

If more than the conditions are true this statement executes the first one which is true, gives the output, and will not write any error only write the warning(that more than one statement is true).
If all the statements are false, it will not display any error but will display a warning.

The below lab example will show how unique it is different from the traditional if else statement.

  **Syntax** -  
`               unique if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `elseif(condition)begin  `  
               `Statements;  `  
               `end  `  




**lab link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/unique_if/unique_if_code.sv  

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/unique_if/unique_if_code_output.log  


***
###  unique0 if 

This statement is the same as the if condition statement when only one condition is true in the whole code. 

If more than one condition is true, it will read the first true condition and display the output without any error but display a warning (more than one condition is true ).
If more than one condition is false, it will not display any output, not even any error and warning.

The below examples will show the difference between the unique0 if and traditional if else condition.

  **Syntax** -    
`               unique0 if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `else if(condition)begin  `  
               `Statements;  `  
               `end  `  
  

**lab links**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/unique0_if/unique0_if_code.sv  


***
###  priority if 

This is again an updated version of the if-else condition statement . When only one condition is true, it will work the same as the if else condition. 

When more than one condition is true, it will execute the first true condition and gives the output and it will not display any error not even a warning.

When all the conditions are false it will display only a warning. 

The below example will properly show the working idea of the priority if condition.

**Syntax** -    
`               priority if(condition)begin  `  
               `Statements;  `  
               `end  `  
               `else if(condition)begin  `  
               `Statements;  `  
               `end  `  
              
              
  
**lab link**   
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/priority_if/priority_if_code.sv  

**lab output link**   
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/if_variants/priority_if/priority_if_code_output.log


***




## case 
The case statement allows us to execute the code for the particular case expression. 
This will give the proper structure for a long code and decrease the complexity of the code also.  
There are three updates for the case statement in the system Verilog and these are -  
1. unique case  
2. unique0 case  
3. priority case  

***
### unique case 

In this, if all the case condition is false, it will display a warning (no match is found for the case statement ) with no error.
If all the conditions are true or more than one is true, it will read the first right or matched case condition and will display the output with one warning and no error.

**Syntax**-  
`            unique case(condition)  `  
            `condition_1: Statements ;  `  
            `.......`  
            `conditon_N:  Statements;  `  
            `endcase  `  

**lab link** 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/unique_case/unique_case.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/unique_case/unique_case_log.log
 


     

***
### priority case 

In this type of case statement, if more than one case condition is true, it will display the output without giving any error with no warning.

**Syntax**-  
`             priority case (condition)  `  
             `case_1: statement;  `  
             `----  `  
             `case_N: statement ;  `  
             `endcase `  
   
**lab link** - 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/priority_case/priority_case.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/priority_case/priority_case_log.log


***















## Loops 

The loops have a sequence of instructions, it will execute when the instruction is true and execute until the condition of the loops will not false. When the condition becomes false, the loops will terminate. 
There are various kinds of loops  -
 


![Loops](https://user-images.githubusercontent.com/110447788/186894792-61b4d18d-35b4-4f25-897b-f556f88acd0f.png)

                           Figure.3. Loops

***



### 1. for 
for loop, execute the statements multiple times until the statement become false. Execution of "for loop" requires three steps -

a. Initialization - It will first initialize the variable.
b. condition -  give condition to the loops. It will decide the purpose of the loop.
c. modifier - means in this part, the increment or decrement is done.

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

This loop is the updated version of for loop in the system Verilog. As compared to for loop, foreach loop syntax is less complicated.
When the condition is true, the statements of the loop execute until the condition becomes false same as for loop.

**Syntax** -    
`               foreach(variable[iterator])begin  `  
               `Statements;  `  
               `end   `  

The below example will give the working idea of foreach loop.

**lab link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/foreach/foreach_loop.sv

**lab output link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/foreach/foreach_loop_log.log

***
 
### 3. forever loop
As the name says forever loop will execute the statements inside the loop forever.  
It can be said an indefinite iteration.

**Syntax** -   
`           forever begin  `  
           `multiple statements;  `  
           `end  `  
  
The below example gives the idea of the working of a forever loop.

**lab link** -   
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/forever_loop/forever_code.sv  

**lab output link**    
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/forever_loop/forever_loop_output.log  



***

### 4. while

In this loop, the first condition is checked, if it is true and the statements inside the while loop will execute until the condition become false.

**Syntax** -   
`               while(condition)begin              `  
               `Statements;  `  
               `end  `  
The below example will give an idea about the working of the while loop.

**lab link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/while/while_code.sv  

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/while/while_loop_output.log  


***
 ### 5. do-while 
A do while loop first executes the statements once, and then checks for the condition is be true. If the condition is true, the set of statements is executed until the condition turns out to be false. If the condition is false, the loop ends right there.


**Syntax** -  
`                 do begin                 `  
                 `Statements;           `  
                 `end                  `  
                `while(condition)begin     `  
                `Statements;  `  
                `end  `  

**lab link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code.sv  

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code_output.log  

***

### 6. break 
 
A break is used to terminate any loop. Generally, we use break after giving the condition in code using the if statement.

We can use break statements in any loop(for, while, do-while), for terminating the execution of a loop. It is always used inside the loop.

**Syntax** - `break;`  

The below example will show, how to terminate the loop using the break statement.

**lab link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue_log.log

***

### 7. continue 

This statement is generally used for skipping the statements in the loop. It is also used inside the loops.

**Syntax** - `continue;`   

The below example will show how the continue statement work. 

**lab link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue_log.log

***

### 8. repeat 

This loop is used for repeating statements or operations for fixed number of times.

**Syntax** -  
             `repeat(no. of times)begin  `  
             `statements;  `  
             `end  `  

**lab link** - 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_code.sv  

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_loop_output.log   


***

## Blocking and non-blocking statement - 
### Blocking statement  
Blocking statements are assigned with =. It will execute serially in procedural blocks. Blocking statements are executed in a block in a sequential manner but when more than two procedural blocks, these statements will execute parallelly in the blocks and will not block the statements of other procedural blocks.

**Syntax** -  
`            variable_name(LHS) = expression(RHS);`  

For a better understanding of Blocking statements go through the following lab
**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/blocking_swap/blocking_swap.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/blocking_swap/blocking_swap_log.log

***

### Non - blocking statement  

 Non-blocking statements are assigned with the <=. It will not block the execution of a statement inside that particular block.
These statements will execute the parallel inside that particular block. 

**Syntax** -  
`             Variable(LHS) <= Expression(RHS) ; `  

For a better understanding of Blocking statements go through the following lab
**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/non_blocking_swap/non_blocking_swap.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/non_blocking_swap/non_blocking_swap_log.log



***


## Function and task 

S.No.|Function | Task |
:-----|:--------|:------|
1.|  Not have timing control statents| have timing control statements|
2.|  Can return a single value | It won't return but affect the values globally |
3.|  Can call only other functions, not tasks .|Can call other tasks and functions both.|





***

### Function 

The function is the subroutine that contains procedural code.
The purpose of the function is to return the value that can be used in the expression.
The function cannot have time control statements like #, @, or fork-join( The function must execute in zero time).
A function can call other functions, not other tasks.
A function can have at least one argument which is to be returned.


**Syntax** -  
  `function data_type function_name(arguments )`  
`    <Statements>;  `  
    `endfunction  `  

Arguments are of two types - 
1. formal argument - declare in the routine header.

2. actual argument - value and function passed to and from the routine.

We can call the function mainly in two ways -
1. call by value   
2. call by reference  

### call by value 

In argument pass by value, the argument passing mechanism works by copying each argument into the subroutine area.

If any changes to arguments within the subroutine, those changes will not be visible outside the subroutine.

The below example will show a clear overview of the working of the call by value function.

**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_value/function_by_value.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_value/func_by_value_log.log

***

### call by reference 

In this, the reference to the original argument is passed to the subroutine. As the argument within a subroutine is pointing to an original argument, any changes to the argument within the subroutine will be visible outside.

The below example will show the clear idea.


**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_ref/function_by_ref.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_ref/func_by_ref_log.log


***

 ## task 

The task is used to split the code into small parts same as the function but there are some differences between them.  
In task , we can provide time delays like # , @ .etc.  
The task can call other tasks and functions also.
The task will not return any value.
We can assign input, output,inout arguments in tasks.
 

There are generally two types of tasks we use -  
1. Static task   
2. Automatic task  


***

### Static task 

 Any task is defaultly static task in which overriding will be there.

**Syntax** -  
`task task_name(arguments)`  
`Statements;  `  
`endtask  `  

**lab link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/tasks/static_task/task.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/tasks/static_task/task1.log

***

### Automatic task 

Automatic tasks allocate unique, stacked storage for each task call.

**Syntax** -  
`task automatic task_name(ref arguments)`  
`Statements;  `  
`endtask  `    

**lab link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/tasks/automatic_task/automatic_task.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/tasks/automatic_task/task_auto_log.log

***
## events 

Event is used for synchronization between two or more concurrently active processes. Initially, we need to declare the event and then it needs to be triggered by using the -> or ->> operator.

Processes can wait for the event by using the @ operator or wait(event_name.triggered).  
when both @ and wait comes at the same point then a race-around condition occurs in between both.

For a better understanding of events go through the below lab  

**lab link:**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/events/event/event.sv

**lab output link:**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/events/event/event_log.log









 



             
