
## Conditional Statement 
Conditional statement  are used for executing the statements by giving the conditions. These statements until the condition become false . 
There are various types of conditional statements - 
### if 
 This statement is use for giving a single condition and   inside it executing the multiple statements or single statement . This is generally use for comparison of a number or two numbers .

**Syntax** - 
              `if(condition)begin

             statements;

             end`

**log file link**  


***
### if else

This statement , first the compiler goes to the if condition and checks the condition and execute it if it is true  or if "if" condition is not true , the compiler will go to the "else" statement and checks the condition either it is true or not . If the "if" or "else" any one of them is not true , then the compiler show the error .

**Syntax** - 
             `if(condition)begin`

              `statements;`

              `end `

             `else begin `

             `Statements;`

             `end `

**Lab link**




***

### if else ladder 

This statement is use by giving the multiple conditional statements . These statements are 'if elseif elseif .... else' . First the compiler checks the 'if 'condition and execute it if it is true  or if it is false, it will jump to the elseif condition and execute and soo on , at last it will come to else condition . 

**Syntax** - `if(condition)begin`

              `Statements;`

              `end `

              `elseif (condition)begin`

              `Statements;`

              `end`

              `elseif(condition)begin`

              `Statements;`

              `end `

               `...`

               `...`

              `else begin `


              `Statements;`

               `end `

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

  **Syntax** - `unique if(condition)begin`

               `Statements;`

               `end `

              `if else(condition)begin`

               `Statements;`

               `end`




**lab link**  


***
unique0 if 

This statement is same as the if condition statement when only one condition is true in the whole code . 

If more than one condition is true , it will read the first true condition and display the output without any error but display a warning (more than one condition is true ).
If more than one condition is false , it will not display any output , not even any error and warning.

Below examples will show the difference between the unique0 if and traditional if else condition .

  **Syntax** - `unique0 if(condition)begin`

               `Statements;`

               `end `

              `if else(condition)begin`

               `Statements;`

               `end`
  

**lab links**


***
priority if 

This is again a update version of if else condition statement .When only one condition is true , it will work same as the if else condition . 

When more than one condition is true , it will execute the first true condition and gives the output and it will not display any error not even warning.

When all the conditions are false it will display only a warning . 

Below example will properly show the working idea of the priority if condition .

**Syntax** - `priority if(condition)begin`

               `Statements;`

               `end `

              `if else(condition)begin`

               `Statements;`

               `end`
              
              
  
**lab link**


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

**Syntax** - `for (initialization; condition; modifier) begin`

             `Statements;`

            `end `

**lab link**


*** 
2. foreach

This loop is the update version of for loop in system verilog . As compare to for loop , foreach loop syntax is less complicated .
When the condition is true , the statements of the loop execute until the condition become false same as for loop .

**Syntax** - ` foreach(variable[iterator])begin `

              `Statements;`

              `end `

Below example will give the working idea of foreach loop .

**lab link** -


***
 
### 3. forever loop
As the name says forever loop will execute the statements inside the loop forever.  
It can be said as indefinite iteration.

**Syntax** - `forever  `

            `begin  `

            `multiple statements;  `

            `end  `
  
Below example gives the idea of the working of foreach loop .

**lab link** -


***

4. while

In this loop , first condition is checked , if it is true and the statements inside the while loop will execute until the condition become false .

**Syntax** - `while(condition)begin`
            
             `Statements;`

              `end `
Below example will give the idea about the working of the while loop.

**lab link** -


***
 5. do while 

This loop will execute the condition first and then checks the condition . Then if the condition is true , the statement inside the while loop will execute until the condition become false .

do while loop execute the statements atleast once if the condition is false .

**Syntax** -
                `do begin`
               
                 `Statements;`
         
                 `end `
                
               `while(condition)begin`
   
                `Statements;`

               `end `

**lab link** -


***

6. break 
 
Break is use to terminate the any loop . Generally, we use break after giving the condition in code using the if statement.

We can use break statement in any loop(for , while , do-while), for terminating the execution of loop . It is always use inside the loop.

**Syntax** - `break;`

Below example will show ,how to terminate the loop using the break statement .

**lab link** -


***

7. continue 

This statement is generally use for skipping the statements in the loop . It is also use inside the loops .

**Syntax** - `continue;` 

Below example will show how the continue  statement work . 


***

8. repeat 

This loop is use for the repeating of statements or operation for fix number of times .

**Syntax** - `repeat(no. of times)begin `

             `Statements;`

             `end `

**lab link** - 


***




             

