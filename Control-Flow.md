   
![Untitled Diagram-Page-2 drawio (6)](https://user-images.githubusercontent.com/110447788/187111580-998e981a-05a0-46d1-81a3-67909da81011.png)




           
                                     Figure.1. Control Flow  
# Control flow 
## Conditional Statements  
Conditional statements are used to check whether the statements in the blocks are executed or not. Conditional statements create the block of statements. If the expression given is -   
**true** - Execute the set of statements in the block.  
**false** - the statements inside that block will not be executed.  
**else** - if the expressions are false then the else block statements will execute at last. 

There are different types of conditional statements. These are --  
### 1. if without else  
flow chart -  
This conditional statement is used for the basic codes where only need to make a decision by giving one condition. If the expression in the condition is -  
**true** - execute the statements in the block.  
**false** - will not execute the statement.  

**Syntax**    
`if(condition)begin  `  
`Statements;  `  
`end  `  

_Note_  
For more than one statement in conditional blocks, need to use begin end block. Statements inside the begin end block execute in a sequential manner.  

**Example**  - Here, the variable declare is a and value assigned to it is 10. The compiler will check the if conditional expression and condition is true a=10. So, the compiler will execute the set of statements inside the if block.     
**Code snippet**  
`bit [3:0]a;`   
`initial begin`  
    `a=10;`  
   `$display ("Value of a = %0d",a);`  
   `if (a==10)begin`  
      `$display ("if expression is true , Successfully entered into the if block");`  
      `$display ( "a is equal to 10 " );`  
    `end`  
     `$display("out of if block");`  
  `end`  

**Output snippet**  
***

### 2. if else 
This conditional statement has two sets of statements, one in the if block and another in the else block. If the expression in the `if` block is true, statements inside it will execute or if the expression is false, statements inside the `else` block will execute.  
`else` block doesn't check any expression to execute statements inside it, it just executes after if the expression is false.  
**Syntax**  
`if(condition) begin  `  
`Statement1;`  
`Statement2;`  
`------`  
`StatementN;  `  
`end  `  
`else begin  `  
`Statement1;  `  
`Statement2;  `  
`---------  `  
`StatementN;`  
`end `  
  
**Example**  - Here the variable declares a is byte type(signed) and the value assigned to it is -1. If conditional expression is false as a is less than 0  

`byte a;`  
`initial begin`  
  `a = -1;`  
  `$display ("Assign the value of a = %0d ",a);`  
  `$display("-------------------------------------");`  
  `if(a>0)begin //false`    
    `$display ("Successfully enters into if block");`    
    `$display ("a is a positive number");`  
    `$display ("----------------------------------");`   
  `end`   
  `else`  
    `$display ("Number is negative");`  
  `$display ("Out of if else block");`  
`end`  

 

***
 
### 3. if else ladder  
This conditional statement helps us to decide among multiple options or expressions. As soon as the expression becomes true, the statements inside it execute and the remaining code blocks are bypassed. If none of the expressions is true, the else block executes.   
else block is an optional block in the ladder. It is used to avoid confusion in code.  
**Syntax**  

`if(condition) begin  `  
`Statement1;`  
`Statement2;`  
`------`  
`StatementN;  `  
`end  `  
`elseif begin  `  
`Statement1;`  
`Statement2;`  
`------`  
`StatementN;  `  
`end   `  
  
`else begin  `  
`Statement1;  `  
`Statement2;  `  
`---------  `  
`StatementN;`  
`end `  

**Example**  
**without else**  
Sequentially all the conditional expressions will be checked. The compiler will execute the set of statements which has valid condition expression. 
**Example**  - Below example has three variables a,b and c. The value assigned to them is 10,12 and 13. the compiler will check the conditional expression one after the other. Here the second conditional expression is true or valid. The output will be the set of statements inside the else if block. 


`int a,b,c;`  
`initial begin`  
 `a = 10;`  
 `b = 12;`  
 `c = 13;`  
 `$display ("Assign the value of a = %0d , b= %0d , c =%0d  " ,a,b,c);`  
 `$display ("------------------------------------------------------");`  
 `if (a>b)begin //false`    
   `$display ("Successfully enters into if block ");`  
   `$display ("Value of a < b");`  
   `$display ("----------------------------------");`  
 `end`  
 `else if (b<c)begin //true`  
   `$display ("Successfully enters into else if block ");`  
   `$display ("value of b<c");`  
   `$display ("----------------------------------------------------");`  
   `end`  
   `else if (c<0) begin //false`    
     `$display ("Successfully enters into second elseif block ");`  
     `$display ("c is a negative number ");`  
     `$display ("--------------------------------------------");`  
   `end`  
   `$display ("Out from ladder block");`  
 `end`  
**output snap**  
 
**with else**  
When none of the conditional expressions is true, the compiler will execute the set of statements of the else block.   
**Example**  
Here the example shows the execution of the else block.   
**Code snippet**  

`int a, b,c;`  
`initial begin`  
 `a = -12;`  
 `b = 12;`  
 `c = 10;`  
 `$display ("Assign the value of a =%0d  b = %0d  c = %0d ", a,b,c);`  
 `$display ("------------------------------------------------------");`  
 `if (a>0) //false condition`    
 `begin`   
 `$display ("Entered into if block ");`  
 `$display ("a is a negative number");`  
 `end`  
 `else if (a==0) begin  // false condition`  
   `$display ("Entered into first elseif block ");`  
   `$display ("a is a negative number ");`  
 `end`  
   `else if (b<c)begin // false condition`  
     `$display ("Entered into second else if block ");`  
     `$display ("b is less than c ");`  
   `end`  
   `else begin`  
     `$display ("None of the condition is true in if-else if blocks ");`  
     `$display ("-------------------------------------------------");`  
   `end`  
   `$display ("Out of the conditional block ");`  
 `end`  
**output snippet**

***
In SystemVerilog, there are three versions of a conditional statement updated. These are -  
### 4. unique if   
This is the updated conditional statement. In a unique if conditional statement, unlike the if-else block the compiler read all the blocks sequentially whether the block is true or not.  
**Syntax**  
`unique if(condition)begin  `  
`Statements;  `  
`end   `  
`else if (condition) begin  `  
`Statements;  `  
`end  `  
`else if (condition) begin  `  
`Statements;  `  
`end  `  
 

There are three possibilities to know the working of a unique if block and these are   
**a. Only one expression is true**     
If only the expression is true unique if conditional statement will work the same as the basic if else block. The output will be the, set of statements inside the block which is executing.  
    
**Example **- Below example shows the three conditional blocks unique if, else if, else if. Here, there are two variables declared one is bit type and the other is int type.  
size() is a default function of SV, use to get the size of the given variable. The size of a is 5 and b is 32 (default size if int data type ). So, the size of b is greater than a, which means unique if the conditional expression is true. Then, the compiler jumps from the conditional block code and does not execute other conditonal blocks (else if blocks).  

` bit [4:0] a;`  
 `int b ;`  
 `initial begin`  
 `unique if ($size(a)<$size(b))begin //True  `  
   `$display ("Inside the unique if block");`  
   `$display ("The size of a is smaller than b ");`  
 `end`  
 `else if ($size(a)==$size(b)) begin //False`  
   `$display ("Inside the first else if block");`  
   `$display ("Size of a = Size of b");`  
 `end`  
 `else if ($size(a)>$size(b))begin //False`  
   `$display ("Inside the second else if block");`  
   `$display ("Size of a is greater than the size of b ");`  
 `end`  
 `$display ("Out from conditional block ");`    
`end`  

**output snap**









 
**b. None of the conditions is true**  
**flow chart**  
with else -  else block statements execute.  
Example - Below example shows the execution of a set of statements inside the else block.  
Here, the variable is money, and the value assigned to the variable is 900. First conditional statements unique if will be false because money is less than 1000. Then, the compiler will check the else if condition and again condition becomes false. Then, the compiler at last will execute the else block.   
The output will be the set of statements inside the else block.    
**Code snippet**  

`int  money;`  
`initial begin`  
  `money = 900;`  
`$display ("Money in account  = %0d",money);`  
`$display ("------------------------");`  
`unique if (money>1000)begin //false`  
  `$display ("Inside the unique if block ");`  
  `$display ("can withdraw money  ");`  
`end`  
`else if (money==0)begin //false`  
  `$display ("Inside the first else if block ");`  
  `$display ("Account block .");`  
`end`  
`else`  
  `$display ("Money withdrawal not allowed .");`  
  `$display ("--------------------------------");`  
  `$display ("Out of the conditional block ");  
  
`end`  



**without else** - The compiler will read all the conditional blocks and gives a warning.  
 **Example **-  Below example shows execute of code with the else block.    
Here, the variable is a and the value assigned to it is 13. Now, the compiler will check the condition sequentially. First, the unique if conditional expression will be checked. As  (a %2) is not equal to 0 so, this conditional expression becomes false. Then, the compiler will go to first else if block and as (a>2) again the conditional expression becomes false. Then, the compiler will check for the next else if block and as a is not equal to 13 again condition becomes false. At last, the compiler will jump from the conditional block and executes the statements outside the conditional blocks.   
**code**           

`initial begin` 
  `a =13;`  
  `$display ("The value of a = %0d", a);`  
  `$display ("------------------------");`  
  `unique if (a%2 == 0)begin  // false`  
    `$display ("Inside the unique if block ");`  
    `$display ("a is an even number");`  
  `end`     
  `else if (a <2)begin // false`  
  `$display (" Inside the else if block ");`  
  `$display ("a is smaller than 2 ");`  
`end`  
`else if (a !=13) begin // False`  
  `$display ("Inside the second else if block ");`  
  `$display ("a is not equal to 13 ");`     
`end`  
`$display ("Out of the conditional block ");`    

`end`  

  **output snap**


**c. More than one condition is true**  
The compiler read all conditional blocks sequential whether the expression is true or not. If more than one conditional block is valid, the output compiler executes the statements which are inside the first valid block. The output will be the set of statements inside the first true conditional block that also gives a warning.  
**Example** - Here the variable declaration is "a" and value assigned to it is 12. The compiler will check the first condition, as (a%2==0) is true and then the compiler will execute the unique if conditional block statements. But, here the compiler task is not finished yet. The compiler will go to the next conditional blocks and will check the conditional expression. As both else, if the conditional statement is true because a >0 and a = 12. After that, the compiler will come out from the conditional blocks and executes the statements from the conditional block.  
The output will be the set of statements of unique if block and one warning are also there.           
**Code snippet**  
`bit [3:0] a;`  
`initial begin`  
  `a = 12;`  
  `$display ("The value of a = %0d", a);`  
  `$display ("------------------------");`  
  `unique if (a%2 ==0)begin`  
    `$display ("Inside the unique if block ");`  
    `$display ("a is an even number.");`  
  `end`  
  `else if (a>0)begin`  
    `$display ("Inside the first else if block ");`  
    `$display ("a is a positive number");`  
  `end`  
  `else if (a ==12)begin`  
    `$display ("Inside the second else if block ");`  
    `$display ("Value of a =12");`  
  `end`  
  `$display ("Out from the conditional blocks");`  
  `$display ("---------------------------------");`    

`end`    
 
**Output snap**  



**Uniqueif v/s if** 
|S.No|uniqueif|if|
|:----|:-------|:--|
|1.|





### 5.unique0if  
Unique0if is the same as unique if but unlike unique if does not report a violation if none of the conditions is true. unique0if is not synthesizable because it does not display a warning in the output, so the programmer can't be able to read the dead code or the error in the code properly.  
**Syntax**  
`unique0if(condition)begin  `  
`Statements;  `  
`end   `  
`else if (condition) begin  `  
`Statements;  `  
`end  `  
`else if (condition) begin  `  
`Statements;  `  
`end  `  

**Example** - Below example show the working of unique if condition.  
Here, the variable declared is age and the value assigned to it is 17. The compiler will check all the conditional expression and as we can see all the conditional expression is false. So, as the output, after simulation, there will be a set of statements which are out from the conditional block.   


`int  age;`  
`initial begin`  
  `age = 17;`  
  `$display ("The age of the person = %0d ",age);`  
  `$display ("----------------------------------");`  
`unique0 if(age >18)begin // false`  
    `$display ("Inside the unique 0 if block ");`  
    `$display ("Eligible for voting");`  
  `end`  
  `else if(age>30) begin //false`  
    `$display ("Inside the first else if block ");`  
    `$display ("Eligible as candidate for PM election in India ");`  
  `end`  
  `else if(age ==10)begin // false`  
    `$display ("Inside the second else if block ");`  
    `$display ("Wait for 8 years more. ");`    
`end`  
`$display ("Out from the conditional block ");`  

`end`  

**output snap**

***

### 6.priority if   
priority if executes conditions sequentially. It is also the same as if-else conditional statement but there are some differences. Below explanation will give a clear picture of how the priority if block work.
**Syntax**  
`priority if (cond_expression)begin  `  
`Statements;  `  
`end  `  
`else if (cond_expression)begin  `  
`Statements;  `  
`end  `  
`-------`  
`else begin //(optional) `  
`Statements ;`  
`end `  







To get the clarity of working on priority if, three conditions are specified and these are -    
**a. only one conditional expression is true**   
 When only one condition is true, the priority if block is as same as the if else if ... block.  

**Example**  
Here, there are three variables declared a,b, and c. The default size of the int data type is 32 bits and the byte is 8 bits. $bit() is the default function of System Verilog which will give the size of the variable. The value assign to a=10 ,b=12 and c =13. First, the priority if the block expression is false because the value of a is not equal to the size of a (12 != 32) and then the compiler will check the next statement. The first else if the condition is true because both a and c are of the same data type.  
As the output, the execution of statements inside the first else if block.  
It is just the same as the if else if block.  
**Code**    
   
`int a;`  
`byte b;`  
`int c;`  
`initial begin`  
 `$display ("The default size of a = ",$bits(a));`  
 `$display ("The default size of b = ",$bits(b));`  
 `$display ("The default size of c = ",$bits(c));`  
 `$display ("-----------------------------------");`  
 `a = 10; //assign value`  
 `b= 12;  // assign value`  
 `c=13;   // assign value`  
 `priority if (a == $bits(a))begin //false`  
   `$display ("Inside the priority if block");`  
   `$display ("Here , value assign to a = default size of a ");`  
  `end` 
 `else if ($bits(a)== $bits(c))begin //true`  
   `$display ("Inside the first else if block ");`  
   `$display ( " Default size of a = default size of c ");`  
 `end`  
 `else if (a>b)begin //false`  
   `$display ("Inside the second else if block ");`  
   `$display ("value of a is greater than b ");`  
 `end`  
 `$display ("-----------------------------");`  
`$display ("Out from the block ");`  
`end`  

**Output snap**  


**b. More than one conditional expression is true**  
The compiler will check the conditional expression sequentially. It will execute all the statements and after simulation, the output will be a set of statements inside the first true conditional block with no warning.  
**Example** - Here, the variable is a,b and c and value assigned to it is 10,20 and 30. We can see the first conditional expression a>b is false. Then, the compiler will check the next block. First and second else if block both have true conditional expression. But, the compiler only checks the first true expression, executes it and comes out from the conditional block. The output will be the set of statements inside the first true else if block with no warning.  
**Code** 


`int a,b,c;`  
`initial begin`  
  `a = 10;`  
  `b =20;`  
  `c = 30;`  
`$display ( "The value of a =%0d  b = %0d  c = %0d ", a,b,c);`  
`$display ("-----------------------------------------------");`  
`priority if (a>b)begin //false`  
  `$display ("Inside the priority if block ");`  
  `$display (" a <b");`  
`end`  
`else if ( b <c )begin //true`  
  `$display ("Inside the first else if block");`  
  `$display ("b<c");`  
`end`  
`else if (a <c )begin //true`  
  `$display ("Inside the second else if block ");`  
  `$display ( "a < c ");`  
`end`  
`$display ("Out from the conditional block ");`  
`end`  

**output snap** 

**c.none of the condition is true**  

**c1. without else**  
When none of the conditional expressions is true, the compiler will come out from the conditional blocks and execute the statements which are out from the conditional blocks.  
**Example** - Here, there are three conditional expressions. The compiler checks the conditional expression because all are false. Then, the output will be the set of statements out from the block.    

`int bill;`  
`initial begin`  
  `bill = 6000; // assign the value`  
  `$display ("Total bill = %0d",bill);`  
  `$display ("------------------------");`  
  `priority if (bill < 1000)begin // false`  
    `$display ("Inside the priority if ");`  
    `$display ("No discount");`  
  `end`  
  `else if (bill ==8000)begin //false`  
    `$display ("Inside the first else if block ");`  
    `$display ("10% discount available ");`  
  `end`  
  `else if (bill >8000)begin // false`  
    `$display ("Inside the second else if block ");`  
    `$display ("15% discount available");`  
  `end`  
`$display ("Out from the conditional block");`  
`$display ("Do more shopping for more discount ......");`  

`end`  

**c2.with else**  
When none of the conditional expressions is true by default compiler to execute the statements which are inside the else block.  
**Example** - In the below example, all the conditional expression is false and then the compiler will execute the statements inside the else block.    

`int bill;`  
`initial begin`  
  `bill = 6000; // assign the value`  
  `$display ("Total bill = %0d",bill);`  
  `$display ("------------------------");`  
  `priority if (bill < 1000)begin // false`  
    `$display ("Inside the priority if ");`  
    `$display ("No discount");`  
  `end`  
  `else if (bill ==8000)begin //false`  
    `$display ("Inside the first else if block ");`  
    `$display ("10 percent  discount available ");`  
  `end`  
  `else if (bill >8000)begin // false`  
    `$display ("Inside the second else if block ");`  
    `$display ("15 percent discount available");`  
  `end`  
  `else begin`  
    `$display ("Inside the else block ");`  
    `$display ("5 percent discount available ");`  
  `end`  
  `$display ("Out from the conditional block");`  
  `$display ("Do more shopping for more discount ......");`  

`end`  

**output snippet**  


***
###  Difference between conditional statements  
|S.No.|Condition| if elseif |unique if|unique0 if|priority if|
|:-----|:-------|:----------|:--------|:----------|:----------|
| 1.| only one conditional expression is true|execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |
|2.|more than one conditional expression is true|executes the first true conditional block statements, no warning display |executes the first true conditional block statements, a warning display |executes the first true conditional block statements, a warning display |executes the first true conditional block statements, no warning display | 
|3.|none of the conditional expressions is true without else |execute the statements out from the conditional block, no warning display |execute the statements out from the conditional block, a warning display |execute the statements out from the conditional block, no warning display |execute the statements out from the conditional block, a warning display | 
|:---|:---|:-----|:-----|:----|



***  
## Purpose of warning    
The unique if, unique0 if and priority if are the updated versions of if-else conditional statements in the system Verilog. These conditional statements display the warning which helps to detect the dead code or unused conditional statements. 


### Dead code  
Dead code is code that doesn’t have any effect on your simulation or synthesis. Examples of dead code are signals that are never used or conditions that are never triggered.

Dead code does not bother the simulator or the synthesis tool. However, it consumes the mental energy of anybody reading the code. People will try to figure out the purpose of a given statement and it may take a while before they realize that they are dealing with a dead code. This makes it more expensive to review code and reuse code. In general, the dead code is a form of technical debt that should be avoided.  

***













***




## case 
 The case statement allows us to execute the code for the particular case expression. This will give the proper structure for a long code and decrease the complexity of the code also. 
  
 Case statement evaluates a given expression and based on the evaluated value(matching a certain condition), it executes the statements associated with it. Basically, it is used to perform different actions based on different conditions. 
     
A system verilog case statement starts with the case keyword and ends with the endcase keyword. A block of multiple statement must be grouped and be within the begin and end statement.

**Syntax:**



        case(condition)
        condition_1: Statements ;
        condition_2: Statements ;
        ...........
        conditon_N: Statements;
        default   : Statements;
        endcase

### Example:         
            x = 2'b01;
            case(x)
            00 : $display("Value of x = %0b", x);
            01 : $display("Value of x = %0b",x);
            10 : $display("Value of x = %0b",x);
            11 : $display("Value of x = %0b" ,x);
            default : $display("Value of x is not find");
            endcase

In the above example,  here expression= "x" should match with one of the case items. In this '01' value is given to the x so the case item '01' is match with the expression = 'x'. This will print the value of x = 1


**Flowchart:**

![Untitled Diagram drawio (23)](https://user-images.githubusercontent.com/110447788/188362145-06201cc7-c397-4b46-b399-afb77f1dcc5e.png)



![Untitled Diagram-Page-5 drawio (1)](https://user-images.githubusercontent.com/110447788/188300504-805f8740-4cf9-41c7-be1a-6c50a2986b45.png)

In the above output, the case statement will execute for all conditions and be true for one of the conditions. This will print the Value of x = 1 in the output

**lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/case/case.sv

**lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/case/case_op.log

### Using of Case statement without default:   
In case statement, default statement is used. The default statement is optional, and there can be only one default statement in a case statement.     
If none of the given case conditions is true, the statement within the default statement is executed.    
Execution will exit the case block without doing anything if none of the items matches the condition and a default statement is not given.

**Syntax:**

            case(condition)  
            condition_1: Statements ;   
            condition_2: Statements ;  
            ...........  
            conditon_N: Statements;  
            endcase  


**Example:**
 
              x = 2'b01;  
              case(x)  
              00 : $display("Value of x = %0b", x);  
              01 : $display("Value of x = %0b",x);  
              10 : $display("Value of x = %0b",x);  
              11 : $display("Value of x = %0b" ,x);  
              endcase  

In the above example, a case statement is used without the default statement. Default statement is used when none of the conditions is true. In this one of the conditions is true and it will print the value of x is '1'    
In this example, if none of the case conditions is true or no default statement is not given then execution will exit the case block without doing anything 

**Flowchart:**

![Untitled Diagram drawio (24)](https://user-images.githubusercontent.com/110447788/188387249-68cd086b-7cd0-4ec8-97cc-5d96d511eeb8.png)

![Untitled Diagram-Page-2 drawio (8)](https://user-images.githubusercontent.com/110447788/188394434-8c70750b-388b-4537-a9d8-f7c7db2f507d.png)

 In the above output, case statement is used without default statement .In this one case condition is true, at the time of execution the output will come to 'Value of x = 1'.If none of the conditions is true or the default statement is not given then the execution will exit the case block without anything.  

**lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_default/case_without_default.sv

**lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_default/case_without_default_op.log

### Use of Break statement inside the case statement:

the break statement is not allowed to use within the loops. while using a break inside the case statement, an error has occurred.

![Untitled Diagram-Page-4 drawio (4)](https://user-images.githubusercontent.com/110447788/188432824-01ddb873-d877-44d1-b65d-78116d2b6020.png)
 
In the above output, a break statement is used inside the case statement. System Verilog does not allow the use of a break statement inside the case statement.  
In this, an error will occur.

**lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/break_case/break_case.sv

**lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/break_case/break_case_op.log
 
There are three updates for the case statement in the system Verilog and these are -  
*  unique case  
*  unique0 case  
*  priority case  

***
### 1. unique case 

In this, if all the case condition is false, it will display a warning (no match is found for the case statement ) with no error.
If all the conditions are true or more than one is true, it will read the first right or matched case condition and will display the output with one warning and no error.

**Syntax**-  
`            unique case(condition)  `  
            `condition_1: Statements ;  `  
            `.......`  
            `conditon_N:  Statements;  `  
            `endcase  `    
  
![unique case](https://user-images.githubusercontent.com/110412468/187091083-c944fd23-383f-452b-a357-981b5895b491.png)


**lab link** 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/unique_case/unique_case.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/unique_case/unique_case_log.log
 


     

***
### 2. priority case 

In this type of case statement, if more than one case condition is true, it will display the output without giving any error with no warning.

**Syntax**-  
`             priority case (condition)  `  
             `case_1: statement;  `  
             `----  `  
             `case_N: statement ;  `  
             `endcase `    
  
![priority case](https://user-images.githubusercontent.com/110412468/187091100-fcd0d4fd-7a9d-45cd-b5d7-37fb425f8d77.png)

   
**lab link** - 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/priority_case/priority_case.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/conditional_statement/case_variants/priority_case/priority_case_log.log


***















## Loops 

The loops have a sequence of instructions, it will execute when the instruction is true and execute until the condition of the loops will not false. When the condition becomes false, the loops will terminate. 
There are various kinds of loops  -
 


![Untitled Diagram-Page-6 drawio (2)](https://user-images.githubusercontent.com/110447788/187124383-92b1cd6a-7628-4ddb-9eb0-7378ae8cdce9.png)


                                        Figure.3. Loops

***

S.No.|loops_variants |  
:-----|:--------|
1.|[for](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#1-for)|
2.|[foreach](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#2-foreach)| 
3.|[forever](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#3-forever-loop)|
4.|[while](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#4-while)| 
5.|[do while](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#5-do-while)|
6.|[repeat](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Control-Flow#6-repeat)|


### 1. for 
for loop, execute the statements multiple times until the condition become false. Execution of "for loop" requires three steps -

a. Initialization - It will first initialize the variable.  
b. condition -  give condition to the loops. It will decide the purpose of the loop.  
c. modifier - means in this part, the increment or decrement is done.  

**Syntax** -   
`              for (initialization; condition; modifier) begin  `    
              `Statements;  `    
              `end   `  ##     
  
![for loop](https://user-images.githubusercontent.com/110412468/187091118-b1918f12-53e4-464d-a8e6-593fb5275796.png)


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
  
![foreach](https://user-images.githubusercontent.com/110412468/187091133-a9064005-7a33-4c88-bb60-8af8243b846c.png)


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
  
![forever](https://user-images.githubusercontent.com/110412468/187091144-6641b98e-2f4f-49be-9c47-2038dd8c604d.png)

  
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
  
![while](https://user-images.githubusercontent.com/110412468/187091159-f86d2f2e-1e21-496f-83db-9f7a97133b80.png)


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
  
![do while](https://user-images.githubusercontent.com/110412468/187091173-640712aa-4016-4596-9905-db555569a1e9.png)


**lab link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code.sv  

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code_output.log  

***

### 6. repeat 

This loop is used for repeating statements or operations for a fixed number of times.

**Syntax** -  
             `repeat(no. of times)begin  `  
             `statements;  `  
             `end  `    
  
![repeat loop](https://user-images.githubusercontent.com/110412468/187091201-fa51918b-57e9-4353-bf81-3886311dc947.png)


**lab link** - 
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_code.sv  

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/repeat_loop/repeat_loop_output.log   


***
### break & Continue
 
* break  

A break is used to terminate any loop. Generally, we use break after giving the condition in code using the if statement.

We can use break statements in any loop(for, while, do-while), for terminating the execution of a loop. It is always used inside the loop.
  
* continue 

This statement is generally used for skipping a particular iteration in the loop. It is also used inside the loops.  
Break will comes out of the loop completely but continue skips only the present iteration.

**Syntax** - `break;` / `continue;`   

The below example will show, how to terminate the loop using the break statement.  

![break   continue](https://user-images.githubusercontent.com/110412468/187091194-76deb9e4-4a75-487d-bab3-d9cb12ef614f.png)


**lab link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue.sv

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/break_continue/break_continue_log.log

***


##  Blocking and non-blocking statement - 
* ### Blocking statement  
Blocking statements are assigned with =. It will execute serially in procedural blocks. Blocking statements are executed in a block in a sequential manner but when more than two procedural blocks, these statements will execute parallelly in the blocks and will not block the statements of other procedural blocks.

**Syntax** -  
`            variable_name(LHS) = expression(RHS);`  

For a better understanding of Blocking statements go through the following lab  
  
![block1](https://user-images.githubusercontent.com/110412468/187091224-dd73b66b-3071-4db9-9f46-7e30cc406eeb.png)


**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/blocking_swap/blocking_swap.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/blocking_non_blocking/blocking_swap/blocking_swap_log.log

***
* ###  Non - blocking statement  

 Non-blocking statements are assigned with the <=. It will not block the execution of a statement inside that particular block.
These statements will execute the parallel inside that particular block. 

**Syntax** -  
`             Variable(LHS) <= Expression(RHS) ; `  

For a better understanding of Blocking statements go through the following lab  
  
![non block 1](https://user-images.githubusercontent.com/110412468/187091236-85f24f54-43e4-478f-90bb-f74e9c290c11.png)


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

**Example** - 
 
`module function_tb;`   
`int x;`  
`function int sum(input int a, b);`    
    `sum = a+b;`   
  `endfunction`  
 `initial begin`    
    `x=sum(10,5);`  
`$display("\tValue of X = %0d",x);`    
`end` 
`endmodule:function_tb`   

Here in the above example, adding two integer numbers by calling the function name.  
we declaring the function name 'sum' and function type int data_type and calling the function name inside the module.
   
**output**  
`Value of X= 15;`   


**Void function**  
Void functions are simply functions that have no return value.    
void is used to indicate a null return from the function.    
They can be used wherever a statement is allowed. They cannot be used as part of an expression.  
 
**Syntax**    
`function void function_name;`  

The function 'function_name' is not returning any data but the code will be evaluated inside the function, so this can be of void data type.    

Arguments are of two types - 
1. formal argument - declare in the routine header.

2. actual argument - value and function passed to and from the routine.

We can call the function mainly in two ways -
*  call by value   
*  call by reference  

### call by value 

In argument pass by value, the argument passing mechanism works by copying each argument into the subroutine area.

If any changes to arguments within the subroutine, those changes will not be visible outside the subroutine.

The below example will show a clear overview of the working of the call by value function.  
  

![func by value](https://user-images.githubusercontent.com/110412468/187091280-df74fd46-39cb-4d6b-8809-cc8f1304cea1.png)


**lab link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_value/function_by_value.sv

**lab output link**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/function/function_by_value/func_by_value_log.log

***
 

### call by reference 

In this, the reference to the original argument is passed to the subroutine. As the argument within a subroutine is pointing to an original argument, any changes to the argument within the subroutine will be visible outside.

The below example will show the clear idea.

![func by ref](https://user-images.githubusercontent.com/110412468/187091260-bac486da-c66f-4eaf-8141-4d9729cad264.png)  

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
*  Static task   
*  Automatic task  


***

### Static task 

 Any task is a default static task in which overriding will be there.

**Syntax** -  
`task task_name(arguments)`  
`Statements;  `  
`endtask  `    

![static task](https://user-images.githubusercontent.com/110412468/187091302-7fc2eb75-05c0-48e5-8e9d-51c3db167bff.png)


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
  
![auto task](https://user-images.githubusercontent.com/110412468/187091324-1915f00e-b913-455c-bda0-8952955b01a7.png)


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
  
![event](https://user-images.githubusercontent.com/110412468/187091331-63e67336-758a-4e20-8c7f-fcbb29d74b61.png)


**lab link:**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/events/event/event.sv

**lab output link:**
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/events/event/event_log.log









 



             
