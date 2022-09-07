   
![Untitled Diagram-Page-2 drawio (6)](https://user-images.githubusercontent.com/110447788/187111580-998e981a-05a0-46d1-81a3-67909da81011.png)




           
                                     Fig -1: Control Flow  
# Control flow 
## Conditional Statements  
Conditional statements are used to check whether the statements in the blocks are executed or not. Conditional statements create the block of statements. If the expression given is -   
**true** - Execute the set of statements in the block.  
**false** - the statements inside that block will not be executed.  
**else** - if the expressions are false then the else block statements will execute at last. 

There are different types of conditional statements. These are --  
### 1. if without else  

![if  drawio](https://user-images.githubusercontent.com/110443268/188595474-4f9f67fe-e330-4a4e-9506-9b242cdd7553.png)  
 
                               fig -2: if flow chart

  
This conditional statement is used for the basic codes where only need to make a decision by giving one condition. If the expression in the condition is -  
**true** - execute the statements in the block.  
**false** - will not execute the statement.  

**Syntax**    
`if(condition)begin  `  
`Statements;  `  
`end  `  

_Note_  
For more than one statement in conditional blocks, need to use begin end block. Statements inside the begin end block execute in a sequential manner.  

**Example**  -     
 Here, the variable declare is a and value assigned to it is 10. The compiler will check the if conditional expression and condition are true a=10. So, the compiler will execute the set of statements inside the if block.     

**Code snippet** 
 
    bit [3:0]a;   
    initial begin  
     a=10;  
    $display ("Value of a = %0d",a);  
    if (a==10)begin  
       $display ("if the expression is true, Successfully entered into the if block"); 
       $display ( "a is equal to 10 " );  
     end  
      $display("out of if block");  
    end  

**Output snippet**  
The below figure shows the output of if conditional statement.  
 
<img width="655" alt="1" src="https://user-images.githubusercontent.com/110443268/188662446-3cac3305-0f7a-435c-808e-5ee433a19e4c.png">  

                                  fig -1 : Output - if


**GitHub Lab Code link** 
 
**GitHub lab output link**   



### 2. if else 

![_if else final  drawio](https://user-images.githubusercontent.com/110443268/188595760-4e4b095b-ddaa-48a2-8422-94ed1a650c09.png)  

                                 fig -3: Flow chart-if else 

This conditional statement has two sets of statements, one in the if block and another in the else block. If the expression in the `if` block is true, statements inside it will execute, or if the expression is false, statements inside the `else` block will execute.  
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
  
**Example**  -  
 
Here the variable declares a is byte type(signed) and the value assigned to it is -1. If the conditional expression is false as a is less than 0.    

**Code Snippet**  

    byte a;  
    initial begin  
    a = -1;  
     $display ("Assign the value of a = %0d ",a);  
     $display("-------------------------------------");  
     if(a>0)begin //false    
       $display ("Successfully enters into if block");    
       $display ("a is a positive number");  
       $display ("----------------------------------");   
      end   
      else  
       $display ("Number is negative");  
      $display ("Out of if else block");  
     end  

 **Output Snippet**  
The below figure shows the output of if-else conditional statement.  
  
<img width="661" alt="2" src="https://user-images.githubusercontent.com/110443268/188662765-67e08d46-2cfa-428f-bdc5-c57f473c91bd.png">
      
                           fig -2 : Output -if else

**GitHub Lab Code link**  

**GitHub Lab Output link**  


***
 
### 3. if else ladder   
  
<img width="527" alt="17" src="https://user-images.githubusercontent.com/110443268/188810764-fa42b586-fc92-44aa-9ce7-01a87dc4d10a.png">

                                   fig-4 :flow chart-if else ladder
  
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


**a. without else**  

Sequentially all the conditional expressions will be checked. The compiler will execute the set of statements that has valid condition expression. 

**Example**  -

 The below example has three variables a,b and c. The value assigned to them is 10,12 and 13. the compiler will check the conditional expression one after the other. Here the second conditional expression is true or valid. The output will be the set of statements inside the else if block. 

**Code Snippet**  
  
         int a,b,c;  
         initial begin    
         a = 10;      
         b = 12;   
         c = 13;   
         $display ("Assign the value of a = %0d , b= %0d , c =%0d  " ,a,b,c);    
         $display ("------------------------------------------------------");    
         if (a>b)begin //false      
           $display ("Successfully enters into if block ");  
           $display ("Value of a < b");  
           $display ("----------------------------------");    
          end    
         else if (b<c)begin //true    
           $display ("Successfully enters into else if block ");  
           $display ("value of b<c");  
           $display ("----------------------------------------------------");  
          end    
          else if (c<0) begin //false    
            $display ("Successfully enters into second elseif block ");  
           $display ("c is a negative number ");    
           $display ("--------------------------------------------");  
         end    
        $display ("Out from ladder block");  
        end  
  
**output snippet**  
  The below figure shows the output of if else ladder without else conditional statement.  

<img width="659" alt="4" src="https://user-images.githubusercontent.com/110443268/188663047-5e03f142-8a0e-4f93-a8ee-e2fa4216a2e1.png">  

                                    fig -3: output - if else ladder without else


**GitHub Lab Code link**  

**GitHub Lab Output link**    
 
**b. with else**  
When none of the conditional expressions is true, the compiler will execute the set of statements of the else block.   
**Example**  
Here the example shows the execution of the else block.   

**Code snippet**   

    int a, b,c;  
    initial begin  
    a = -12;  
    b = 12;  
    c = 10;  
    $display ("Assign the value of a =%0d  b = %0d  c = %0d ", a,b,c);  
    $display ("------------------------------------------------------");  
    if (a>0) //false condition    
    begin`   
    $display ("Entered into if block ");  
    $display ("a is a negative number");  
    end  
     else if (a==0) begin  // false condition  
       $display ("Entered into first elseif block ");  
       $display ("a is a negative number ");  
     end  
     else if (b<c)begin // false condition  
       $display ("Entered into second else if block ");  
       $display ("b is less than c ");  
      end  
      else begin  
       $display ("None of the condition is true in if-else if blocks ");  
       $display ("-------------------------------------------------");  
     end  
     $display ("Out of the conditional block ");  
    end  
  
**output snippet**  
The below figure shows the output of the if-else ladder with else conditional statement.     

<img width="659" alt="3" src="https://user-images.githubusercontent.com/110443268/188663392-2b76d206-0fea-45d5-9e18-24efb2c6004a.png">  
               
                                fig -4: Output-if else ladder with else


**GitHub Lab Code link**  

**GitHub Lab Output link**  

***
In SystemVerilog, there are three versions of a conditional statement updated. These are -  

### 4. unique if  
![uniqueif1](https://user-images.githubusercontent.com/110443268/188621317-1834d950-0e08-459b-8c92-4226efee2f21.jpg)

                                    fig-5 :flow chart:unique_if 
   
This is the updated conditional statement. In a unique, if conditional statement, unlike the if-else block the compiler read all the blocks sequentially whether the block is true or not. 
 
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
    
**Example**-   
 The below example shows the three conditional blocks unique if, else if, else if. Here, there are two variables declared one is bit type and the other is int type.  
size() is a default function of SV, use to get the size of the given variable. The size of a is 5 and b is 32 (default size if int data type ). So, the size of b is greater than a, which means unique if the conditional expression is true. Then, the compiler jumps from the conditional block code and does not execute other conditional blocks (else if blocks).   

**Code snippet**  

     bit [4:0] a;  
     int b;  
     initial begin  
     unique if ($size(a)<$size(b))begin //True    
       $display ("Inside the unique if block");  
       $display ("The size of a is smaller than b ");  
     end  
     else if ($size(a)==$size(b)) begin //False  
        $display ("Inside the first else if block");  
        $display ("Size of a = Size of b");  
      end  
      else if ($size(a)>$size(b))begin //False  
        $display ("Inside the second else if block");  
        $display ("Size of a is greater than the size of b ");  
      end  
      $display ("Out from conditional block ");    
      end  

**output snippet**  
The below figure shows the output of the unique if for only one true condition.
<img width="674" alt="5" src="https://user-images.githubusercontent.com/110443268/188663928-def7bbea-b5d0-4b5f-a8a2-75b543f7b6bf.png">  
        
                                 fig -5: output: unique if - only one true condition

**GitHub Lab Code link**  

**GitHub Lab Outputlink**

 
**b. None of the conditions is true**  
 
with else - else block statements execute.

<img width="628" alt="uniqueif _withelsedrawio" src="https://user-images.githubusercontent.com/110443268/188623218-c453b9eb-110f-4f39-ba22-28506ec1493d.png">  

                                  fig -6:flow chart:  with else unique if 
 

Example -  

 The below example shows the execution of a set of statements inside the else block.  
Here, the variable is money, and the value assigned to the variable is 900. First conditional statements unique if will be false because money is less than 1000. Then, the compiler will check the else if condition, and again condition becomes false. Then, the compiler at last will execute the else block.   
The output will be the set of statements inside the else block.  
    
**Code snippet**  

    int  money;  
    initial begin  
    money = 900;  
    $display ("Money in account  = %0d",money);  
    $display ("------------------------");  
    unique if (money>1000)begin //false  
      $display ("Inside the unique if block ");  
      $display ("can withdraw money  ");  
    end  
    else if (money==0)begin //false  
     $display ("Inside the first else if block ");  
     $display ("Account block .");  
    end  
    else  
    $display ("Money withdrawal not allowed .");  
    $display ("--------------------------------");  
    $display ("Out of the conditional block ");  
    end  

**Output snap**  
The below figure shows the output of the unique if -none of the conditions is true with else.  
    
<img width="672" alt="8" src="https://user-images.githubusercontent.com/110443268/188665366-1d4eca95-13ee-4f09-a04c-b151d8dc5221.png">  
  
                                    fig -6: output - unique if -none of the conditions is true with else

**GitHub Lab Code link**  

**GitHub Lab Output link**  

**without else** - The compiler will read all the conditional blocks and gives a warning.  

**Flow chart** - Refer fig -4. 
 
  
 **Example**- 
 
  The below example shows execute of code with the else block.    
Here, the variable is a and the value assigned to it is 13. Now, the compiler will check the condition sequentially. First, the unique if conditional expression will be checked. As  (a %2) is not equal to 0 so, this conditional expression becomes false. Then, the compiler will go to first else if block and as (a>2) again the conditional expression becomes false. Then, the compiler will check for the next else if block and as a is not equal to 13 again condition becomes false. At last, the compiler will jump from the conditional block and executes the statements outside the conditional blocks.  
   
**Code Snippet**             

     initial begin 
      a =13;  
      $display ("The value of a = %0d", a);  
      $display ("------------------------");  
      unique if (a%2 == 0)begin  // false  
        $display ("Inside the unique if block ");  
        $display ("a is an even number");  
      end     
      else if (a <2)begin // false  
       $display (" Inside the else if block ");  
       $display ("a is smaller than 2 ");  
      end  
      else if (a !=13) begin // False  
        $display ("Inside the second else if block ");  
        $display ("a is not equal to 13 ");     
      end    
      $display ("Out of the conditional block ");    
      end  

  **output snap**  
The below figure shows the output of the unique if -none of the conditions is true without else.  
  

<img width="923" alt="7" src="https://user-images.githubusercontent.com/110443268/188665260-eac31337-b4b5-49cc-ba49-0fb853a8c2ea.png">  
 
                                    fig -7: output - unique if -none of the conditions is true without else

**GitHub Lab Code Link**  

**GitHub Lab Output Link**


**c. More than one condition is true** 
 
The compiler read all conditional blocks sequentially whether the expression is true or not. If more than one conditional block is valid, the output compiler executes the statements which are inside the first valid block. The output will be the set of statements inside the first true conditional block that also gives a warning.  
**Example** - Here the variable declaration is "a" and value assigned to it is 12. The compiler will check the first condition, as (a%2==0) is true and then the compiler will execute the unique if conditional block statements. But, here the compiler task is not finished yet. The compiler will go to the next conditional blocks and will check the conditional expression. As both else, if the conditional statement is true because a >0 and a = 12. After that, the compiler will come out from the conditional blocks and executes the statements from the conditional block.  
The output will be the set of statements of unique if block and one warning are also there.  
           
**Code snippet**  
  
     bit [3:0] a;  
     initial begin  
     a = 12;  
     $display ("The value of a = %0d", a);  
     $display ("------------------------");  
     unique if (a%2 ==0)begin  
       $display ("Inside the unique if block ");  
       $display ("a is an even number.");  
     end  
     else if (a>0)begin  
      $display ("Inside the first else if block ");  
      $display ("a is a positive number");  
      end  
      else if (a ==12)begin  
       $display ("Inside the second else if block ");  
       $display ("Value of a =12");  
      end  
      $display ("Out from the conditional blocks");  
      $display ("---------------------------------");    
      end    
 
**Output snap**  
  
The below figure shows the output of the unique if -more than the conditions is true.  
 

<img width="640" alt="6" src="https://user-images.githubusercontent.com/110443268/188664946-63f8f84f-5480-4fa1-a36a-09cccc83593b.png">  
                
                                   fig -8: Output - unique if -more than one condition is true  

**GitHub Lab Code link**  

**GitHub Lab Output link**  

***


### 5.unique0if  

<img width="520" alt="uniqueif1 drawio" src="https://user-images.githubusercontent.com/110443268/188624283-a7feb571-9299-4571-8faf-99250c065ceb.png">

                                  fig -7 :flow chart: unique0_if  

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

**Example** -

 The below example show the working of unique if condition.  
Here, the variable declared is age and the value assigned to it is 17. The compiler will check all the conditional expression and as we can see all the conditional expression is false. So, as the output, after simulation, there will be a set of statements which are out from the conditional block.   

**Code Snippet**  

    int  age;  
    initial begin  
      age = 17;  
      $display ("The age of the person = %0d ",age);  
      $display ("----------------------------------");  
    unique0 if(age >18)begin // false  
        $display ("Inside the unique 0 if block ");  
       $display ("Eligible for voting");  
    end   
    else if(age>30) begin //false  
      $display ("Inside the first else if block ");  
      $display ("Eligible as candidate for PM election in India ");  
    end  
    else if(age ==10)begin // false  
      $display ("Inside the second else if block ");  
      $display ("Wait for 8 years more. ");    
    end  
    $display ("Out from the conditional block ");  
    end  

**output snippet**  
The below figure shows the output of the unique0 if -none of the conditions is true.  


<img width="627" alt="9" src="https://user-images.githubusercontent.com/110443268/188665606-6b9f4e2f-016b-443a-84fe-c05a64d4dba6.png">  

                                       fig-9 : Output-unique0 if

**GitHub Lab Code link**  

**GitHub Lab Output link**  

***

### 6.priority if   

<img width="534" alt="priorityif with else  drawio" src="https://user-images.githubusercontent.com/110443268/188625559-744eb407-e35c-42d3-9d57-9f203782a8cf.png">
   
                                     fig -8: flow chart: priority if

priority if executes conditions sequentially. It is also the same as if-else conditional statement but there are some differences. The below explanation will give a clear picture of how the priority if block works.

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
  
**Code Snippet**      
   
    int a;  
    byte b;  
    int c;  
    initial begin 
     $display ("The default size of a = ",$bits(a));  
     $display ("The default size of b = ",$bits(b));  
     $display ("The default size of c = ",$bits(c));  
     $display ("-----------------------------------");  
     a = 10; //assign value  
     b= 12;  // assign value  
    c=13;   // assign value  
    priority if (a == $bits(a))begin //false  
     $display ("Inside the priority if block");  
     $display ("Here , value assign to a = default size of a ");  
    end 
    else if ($bits(a)== $bits(c))begin //true  
      $display ("Inside the first else if block ");  
      $display ( " Default size of a = default size of c ");  
    end  
    else if (a>b)begin //false  
      $display ("Inside the second else if block ");  
      $display ("value of a is greater than b ");  
    end  
    $display ("-----------------------------");  
    $display ("Out from the block ");  
    end 

**Output snap** 
 The below figure shows the output of the priority if - only one condition is true.  
  
<img width="617" alt="10" src="https://user-images.githubusercontent.com/110443268/188669700-86d998f5-93ad-4823-8f98-1b84ae0217ee.png">  
                 
                                    fig -10:Output-priority if -only one condition is true

**GitHub Lab Code link**  

**GitHub Lab Output link**  

**b. More than one conditional expression is true**  

The compiler will check the conditional expression sequentially. It will execute all the statements and after simulation, the output will be a set of statements inside the first true conditional block with no warning.
  
**Example** - Here, the variable is a,b and c, and the value assigned to it is 10,20 and 30. We can see the first conditional expression a>b is false. Then, the compiler will check the next block. First and second else if block both have true conditional expression. But, the compiler only checks the first true expression, executes it, and comes out from the conditional block. The output will be the set of statements inside the first true else if blocked with no warning.  
 
**Code Snippet**  

     int a,b,c;  
     initial begin  
      a = 10;  
      b =20;  
      c = 30;  
     $display ( "The value of a =%0d  b = %0d  c = %0d ", a,b,c);  
     $display ("-----------------------------------------------");  
     priority if (a>b)begin //false  
       $display ("Inside the priority if block ");  
       $display (" a <b");  
     end  
    else if ( b <c )begin //true  
      $display ("Inside the first else if block");  
      $display ("b<c"); 
    end  
    else if (a <c )begin //true  
      $display ("Inside the second else if block ");  
      $display ( "a < c ");  
    end  
    $display ("Out from the conditional block ");  
    end  

**output snap**  
 
 The below figure shows the output of the priority if - more than one condition is true.  

<img width="629" alt="11" src="https://user-images.githubusercontent.com/110443268/188669964-9897afe8-bdc5-42f6-ab98-773df939fa8e.png">  
 
                                    fig -11: Output -priority if -more than one true condition

**GitHub Lab Code link**

**GitHub Lab Output link**  

**c.none of the condition is true**  

**c1. without else**  
When none of the conditional expressions is true, the compiler will come out from the conditional blocks and execute the statements which are out from the conditional block and display a warning. 
  
**Example** -

 Here, there are three conditional expressions. The compiler checks the conditional expression because all are false. Then, the output will be the set of statements out from the block and display a warning.    

**Code Snippet**

     int bill;  
    initial begin  
     bill = 6000; // assign the value  
    $display ("Total bill = %0d",bill);  
    $display ("------------------------");  
    priority if (bill < 1000)begin // false  
      $display ("Inside the priority if ")  
      $display ("No discount");  
    end  
    else if (bill ==8000)begin //false  
      $display ("Inside the first else if block ");  
      $display ("10% discount available ");  
    end  
    else if (bill >8000)begin // false  
      $display ("Inside the second else if block ");  
      $display ("15% discount available");  
    end  
    $display ("Out from the conditional block");  
    $display ("Do more shopping for more discount ......");  
    end  

**Output Snippet**  

   The below figure shows the output of the priority if - none of the conditions is true without else.  

<img width="926" alt="12" src="https://user-images.githubusercontent.com/110443268/188670397-71956394-1333-44a2-afa6-9c74b4f45427.png">  
     
                                    fig -12:Output - priority if -none of the conditions is true without else


**GitHub Lab Code link**  

**GitHub Lab Output link**  

**c2.with else**  

<img width="534" alt="priorityif with else  drawio" src="https://user-images.githubusercontent.com/110443268/188625559-744eb407-e35c-42d3-9d57-9f203782a8cf.png">
      
                                 fig -9: flow chart: with else priority if

When none of the conditional expressions is true by default compiler to execute the statements which are inside the else block.  
**Example** -      
 In the below example, all the conditional expression is false and then the compiler will execute the statements inside the else block.  

**Code Snippet**      

     int bill;  
     initial begin  
     bill = 6000; // assign the value  
     $display ("Total bill = %0d",bill);  
     $display ("------------------------");  
     priority if (bill < 1000)begin // false  
      $display ("Inside the priority if ");  
      $display ("No discount");  
     end  
     else if (bill ==8000)begin //false  
      $display ("Inside the first else if block ");  
      $display ("10 percent  discount available ");  
    end  
    else if (bill >8000)begin // false  
     $display ("Inside the second else if block ");  
     $display ("15 percent discount available");  
    end  
    else begin  
     $display ("Inside the else block ");  
     $display ("5 percent discount available ");  
    end  
    $display ("Out from the conditional block");  
    $display ("Do more shopping for more discount ......");  
    end  

**output snippet**  
 The below figure shows the output of the priority if - more than one condition is true without else.  
    
<img width="604" alt="13" src="https://user-images.githubusercontent.com/110443268/188670474-2babe11c-8b3c-465f-b3b8-118bc5e2d112.png">  

                               fig -13: Output - priority if -none of the conditions is true without else

**GitHub Lab Code link**  

**GitHub Lab Output link**  

***
###  Difference between conditional statements  
|S.No.|Condition| if elseif |unique if|unique0 if|priority if|
|:-----|:-------|:----------|:--------|:----------|:----------|
| 1.| only one conditional expression is true|execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |execute the set of statements inside the true conditional block |
|2.|more than one conditional expression is true|executes the first true conditional block statements, no warning display |executes the first true conditional block statements, a warning display |executes the first true conditional block statements, a warning display |executes the first true conditional block statements, no warning display | 
|3.|none of the conditional expressions is true without else |execute the statements out from the conditional block, no warning display |execute the statements out from the conditional block, a warning display |execute the statements out from the conditional block, no warning display |execute the statements out from the conditional block, a warning display | 




***  
## Purpose of warning    
The unique if, unique0 if, and priority if are the updated versions of if-else conditional statements in the system Verilog. These conditional statements display the warning which helps to detect the dead code or unused conditional statements. 


### Dead code  
Dead code is code that doesn’t have any effect on your simulation or synthesis. Examples of dead code are signals that are never used or conditions that are never triggered.

Dead code does not bother the simulator or the synthesis tool. However, it consumes the mental energy of anybody reading the code. People will try to figure out the purpose of a given statement and it may take a while before they realize that they are dealing with a dead code. This makes it more expensive to review code and reuse code. In general, the dead code is a form of technical debt that should be avoided.  

***













***




## case 
 The case statement allows us to execute the code for the particular case expression. This will give the proper structure for a long code and decrease the complexity of the code also. 
  
 A case statement evaluates a given expression and based on the evaluated value(matching a certain condition), it executes the statements associated with it. Basically, it is used to perform different actions based on different conditions. 
     
A system verilog case statement starts with the case keyword and ends with the endcase keyword. A block of multiple statements must be grouped and within the begin and end statement.

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

In the above example,  here expression= "x" should match one of the case items. In this '01' value is given to the x so the case item '01' is matched with the expression = 'x'. This will print the value of x = 1


**Flowchart:**

![Untitled Diagram drawio (23)](https://user-images.githubusercontent.com/110447788/188362145-06201cc7-c397-4b46-b399-afb77f1dcc5e.png)

                                  Fig -10: flow chart: case statement with default statement

**Output snippet:**

![Untitled Diagram-Page-5 drawio (1)](https://user-images.githubusercontent.com/110447788/188300504-805f8740-4cf9-41c7-be1a-6c50a2986b45.png)

                                 Fig -14: Output: case statement in which one condition is true

In the above output, the case statement will execute for all conditions and be true for one of the conditions. This will print the Value of x = 1 in the output.

**GitHub Lab Code link**https://github.com/piyushagrawal4578/control-flow/blob/main/case/case.sv
 
**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/case/case_op.log

### Using of Case statement without a default:   
In case statement, the default statement is used. The default statement is optional, and there can be only one default statement in a case statement.     
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

In the above example, a case statement is used without the default statement. A default statement is used when none of the conditions is true. In this one of the conditions is true and it will print that the value of x as '1'    
In this example, if none of the case conditions is true or no default statement is not given then execution will exit the case block without doing anything 

**Flowchart:**

![Untitled Diagram drawio (24)](https://user-images.githubusercontent.com/110447788/188387249-68cd086b-7cd0-4ec8-97cc-5d96d511eeb8.png)
                      
                                       Fig -11: flow chart: case statement without default statement

**Output snippet:**

![Untitled Diagram-Page-2 drawio (8)](https://user-images.githubusercontent.com/110447788/188394434-8c70750b-388b-4537-a9d8-f7c7db2f507d.png)

                                    Fig -15: Output: case statement in which one condition is true

 In the above output, the case statement is used without a default statement. In this one case condition is true, at the time of execution the output will come to 'Value of x = 1'.If none of the conditions is true or the default statement is not given then the execution will exit the case block without anything.  

**GitHub Lab Code link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_default/case_without_default.sv

**GitHub Lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_default/case_without_default_op.log

### Using of range in case statement with the use of inside statement:    

In this, the range is declared in the case statement with the use of an inside statement.    
If we want to give a range value in a case statement, this will be done with help of an inside statement.

**Syntax:**
         
           case(condition) inside
           condition_1: Statements ;
           condition_2: Statements ;
           ...........
           conditon_N: Statements;
           endcase
 

**Example:**

              unique case(x) inside
              [2:3] : $display("Value of x = %0d", x);
              [4:5] :$display("Value of x = %0d",x);
              [6:9] : $display("Value of x = %0d",x);
              [8:9]  : $display("Value of x = %0d" ,x);
              default : $display("Value of x is not found");
              endcase

In the above example, we are declaring a range in a case statement with the use of **inside** statement. In this, they will get the value from the declared range by the use of an inside statement.
**Output snippet:**

![Untitled Diagram-Page-6 drawio (4)](https://user-images.githubusercontent.com/110447788/188553176-7f10aa14-ce7c-4fb6-beca-acd912dd8fbb.png)

                                  Fig -16: Output: case statement with a range

In the above output, the case statement will get executed with the use of an inside statement. The case statement will get executed and displays the output 'Value of x = 6'  

**GitHub Lab Code link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_range/case_range.sv

**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/case_range/case_range_op.log







### Use of Break statement inside the case statement:

the break statement is not allowed to use within the loops. while using a break inside the case statement, an error has occurred.

**Output snippet:**

![Untitled Diagram-Page-4 drawio (4)](https://user-images.githubusercontent.com/110447788/188432824-01ddb873-d877-44d1-b65d-78116d2b6020.png)

                                    Fig - 17: Output: break statement is not allowed inside the case

In the above output, a break statement is used inside the case statement. System Verilog does not allow the use of a break statement inside the case statement.  
In this, an error will occur.

**GitHub Lab Code link** https://github.com/piyushagrawal4578/control-flow/blob/main/break_case/break_case.sv

**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/break_case/break_case_op.log
 
There are three updates for the case statement in the system Verilog and these are -  
*  unique case  
*  unique0 case  
*  priority case  

***
### 1. unique case 

In a unique case, if all the case condition is false, it will display a warning (no match is found for the case statement ) with no error.  
If all the conditions are true or more than one condition is true, it will read the first right or matched case condition and will display the output with one warning and no error.

**Syntax :**

      unique case(condition)
      condition_1: Statements ;
      condition_2: Statements ;
      ............
      conditon_N: Statements;
      endcase

### Example:     
           x = 2'b01;
           unique case(x)
           00 : $display(" Value of x is = %0b", x);
           //01 : $display(" Value of x is = %0b", x);
           10 : $display(" Value of x is = %0b", x);
           11 : $display(" Value of x is = %0b", x);
           endcase
In the above example, the unique case statement is used. Here all the conditions are false, this will print the output with a warning and no error.

**Output snippet:**

![Untitled Diagram-Page-6 drawio (3)](https://user-images.githubusercontent.com/110447788/188300519-a4af7834-91ea-44c9-9f11-c61f7497efbb.png)

                                      Fig - 18: Output: In a unique case, no conditions are true 

In the above output, all the condition is false so the unique case gives a warning with no error.


**GitHub Lab Code link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique_case/unique_case.sv

**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique_case/unique_case_op.log


**Example:**
           
             x = 2'b00;
             unique case(x)
             00 : $display("Value of x is =%0b" , x);
             00 : $display("Value of x is =%0b" , x);
             01 : $display("Value of x is =%0b" , x);
             10  : $display("Value of x is =%0b" , x);
             11  :$display("Value of x is =%0b" , x);
             endcase

In the above example, a unique case statement is used. In the unique case, if more than one condition is true, it will read the first right or matched case condition and will display the output with one warning and no error.    
If these two condition is true, at the time of execution this will take the first matched condition and print the value of x = '0' with a warning(no error)

**Flowchart:** 

![Untitled Diagram-Page-2 (1)](https://user-images.githubusercontent.com/110447788/188631312-47429f33-e575-4f20-977b-2ee272f46f3a.jpg)
        
                              Fig -12: flow chart: unique case statement

**Output snippet:**

![Untitled Diagram-Page-3 drawio (2)](https://user-images.githubusercontent.com/110447788/188424211-6e39fd47-a153-47be-8154-a808116d2dbb.png)
     
                               Fig -19: Output: unique case in which more than one condition is true
 
In the above output, a unique case statement is used. In this more than one condition is true, the unique case will read the first matched condition and will give the Value of x = '0' with a warning (no error).

**GitHub Code Lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique2_case/unique_case2.sv

**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique2_case/unique2_case_op.log

### unique case with default statement

In this, we will use the default statement inside the unique case statement.    
If none of the conditions is true inside the unique case statement then the default statement will get executed.

**Syntax:**

           unique case(condition)
           condition_1: Statements ;
           condition_2: Statements ;
           ............
           conditon_N: Statements;
           default :   Statements;
           endcase 

**Example:**

            x = 2'b01;
            unique case(x)
            00 : $display("Value of x is =%0b" , x);
           // 01 : $display("Value of x is =%0b" , x);
            10 : $display("Value of x is =%0b" , x);
            11 : $display("Value of x is =%0b" , x);
            default  :$display("Value of x is =%0b" , x);
            endcase

In the above example, the default statement is used inside the unique case statement.  
In this, if no conditions of the case statement are true then the default statement will get executed.

**Flowchart:**

![Untitled Diagram-Page-2 drawio (12)](https://user-images.githubusercontent.com/110447788/188619322-f903de48-023e-46cf-9f2d-38b42cfdb295.png)

                               Fig -13: flow chart: unique case with default statement

**Output snippet:**

![Untitled Diagram-Page-5 drawio (2)](https://user-images.githubusercontent.com/110447788/188492977-950cee1a-5762-440c-ba60-fcb911e155ec.png)

                                Fig - 20: Output: no conditions are true, default statement gets executed 

In the above output, there is no condition is true inside the case statement, then the default statement is get executed and prints the 'Value of x = 1'
in the output.

**GitHub Code Lab link**  https://github.com/piyushagrawal4578/control-flow/blob/main/unique_case_default/unique_case_default.sv

**GitHub Lab Output link**  https://github.com/piyushagrawal4578/control-flow/blob/main/unique_case_default/unique_case_default_op.log



## uniuqe0 case

In the unique0 case, if all the case condition is false, it will not display a warning with no error.   
If all the conditions are true or more than one condition is true, it will read the first right or matched case condition and will display the output with one warning and no error.

**Syntax :**

       unique0 case(condition)
       condition_1: Statements ;
       condition_2: Statements ;
       ...........
       conditon_N: Statements;
      endcase


### Example:      
            x = 2'b01;
            unique0 case(x)
            00 : $display(" Value of x is = %0b", x);
            01 : $display(" Value of x is = %0b", x);
            10 : $display(" Value of x is = %0b", x);
            11 : $display(" Value of x is = %0b", x);
            01 : $display(" Value of x is = %0b", x);
            endcase

In the above example, the unique0 case is used. In these two conditions is true and unique0 will read the first right or matched condition and print the output Value of x = "1" with the warning.

**Output snippet:**

![Untitled Diagram-Page-8 drawio (3)](https://user-images.githubusercontent.com/110447788/188300546-eb50b6e6-a5b8-44a4-94fe-e73f828b8e9a.png)

                                    Fig -21: Output: unique0 case in which two conditions are true

In the above output, two conditions are true at a time this will make the case statement not unique, uniquq0 will read the first right matched condition and display the  Value of x is 1 with the warning 


**GitHub Code Lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique0_case/unique0_case.sv

**GitHub Lab Output link** https://github.com/piyushagrawal4578/control-flow/blob/main/unique0_case/unique0_case_op.log

### 2. priority case 

In this type of case statement, if more than one case condition is true, it will display the output without giving any error with no warning.

**Syntax
***
:**  

             priority case(condition)
             condition_1: Statements ;
             condition_2: Statements ;
             ...........
             conditon_N: Statements;
             endcase

### Example:      
            pqr = 5;
            priority case (pqr)
            5 : $display ("Found to be 5");
            5 : $display ("Again found to be 5");
            7 : $display ("Found to be 7");
            endcase

In the above example, the priority case is used. In these two conditions is the right or matched condition so the priority case will read the first right condition and execute it and display the output with no warning and no error.

**Flowchart:**

![Untitled Diagram-Page-2 (2)](https://user-images.githubusercontent.com/110447788/188636662-ce0699fb-568e-4863-b106-6f347b439e50.jpg)

                                Fig -14: flow chart: priority case statement

**Output snippet:**

![Untitled Diagram-Page-9 drawio (4)](https://user-images.githubusercontent.com/110447788/188300570-d5fc26b9-0fac-4499-9cbf-8785c03171f2.png)

                               Fig -22: Output: priority case statement in which two conditions are true

In the above output, more than one condition is true. priority case checks the first right matched condition, executes it, and displays the output without warning and error.

**GitHub Code Lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/priority_case/priority_case.sv

**GitHub Lab Output link**  https://github.com/piyushagrawal4578/control-flow/blob/main/priority_case/priority_case_op.log    













***



## Loops 

The loops have a sequence of instructions, it will execute when the instruction is true and execute until the condition of the loops will not false. When the condition becomes false, the loops will terminate. 
There are various kinds of loops  -
 


![Untitled Diagram-Page-6 drawio (2)](https://user-images.githubusercontent.com/110447788/187124383-92b1cd6a-7628-4ddb-9eb0-7378ae8cdce9.png)


                                        Fig - : Loops

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
              `end   `       
  
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
In a while loop, first we need to check the condition then only we can execute the statements. We need to initialize the variable in the condition before execution.  
A while loop first checks the condition is true and then executes the statements if it is true. If the condition is false, the loop ends right there.     
   
**Syntax** -   
`               while(condition)begin              `  
               `Statements;  `  
               `end  ` 
  

**Flowchart:**

![nanoo dig](https://user-images.githubusercontent.com/110447788/188705046-66e378e6-3057-4bb2-ba48-5fa286c49571.png)

**Code snippet**  

**Output snippet**  

**lab link** -
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/while/while_code.sv  

**lab output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/while/while_loop_output.log  


***
 ### 5. do-while 
In the do-while loop, first execute the condition once and then check whether the condition is true or not. If the condition is true, the set of statements is executed until the condition turns out to be false. If the condition is false the loop ends right there.  

**Syntax** -  
`                 do begin                 `  
                 `Statements;           `  
                 `end                  `  
                `while(condition)begin     `  
                `Statements;  `  
                `end  `    
  
![do while](https://user-images.githubusercontent.com/110412468/187091173-640712aa-4016-4596-9905-db555569a1e9.png)

**Flowchart:**

![nanoo dig2](https://user-images.githubusercontent.com/110447788/188705142-bb1b3c17-ff8c-4de2-9a86-83321afa2670.png)


**GitHub Lab Code link** -  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code.sv  

**GitHub LAb Output link**  
https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/loops/do_while/do_while_code_output.log  

***

### 6. repeat 

This loop is used for repeating statements or operations for a fixed given number of times.  

**Syntax** -  
             `repeat(no. of times)begin  `  
             `statements;  `  
             `end  `    
  

**Example** - Below example shows, the working of the repeat loop. Here, there are three statements inside the repeat loop. the repeating is for 4 times.  
 
**Code Snippet**  
  
    module repeat_code;  
    initial begin ;  
     repeat(4)begin   // Repeat the statements inside 4 times  
       $display ("Good morning");  
       $display ("Keep shining");  
       $display ("--------------");  
     end  
    end  

**Flowchart:**

![repeat](https://user-images.githubusercontent.com/110447788/188849639-db5fe78a-a6d6-43a8-8665-c12a9d51f46b.png)


**Output Snippet**  

<img width="435" alt="15" src="https://user-images.githubusercontent.com/110443268/188803547-7c5ff4fc-8388-45fc-817f-19c431c51943.png">


**GitHub Code Lab link** - 

**GitHub Lab Output link**

**Implementation of repeat loop using for loop**  
We can implement a repeat loop using other loops also. Below example will show the implementation of a repeat loop using for loop.  

**Example** - Same as the above example, here we are repeating these same statements using them for a  loop.  
  
**Code Snippet**  

     initial begin  
      for (int i = 1;i<=4;i++)begin   // for loop initialization, repeat the statements inside it for  
         $display ("Good morning");   // 4 times (i =1,2,3,4)  
         $display ("Keep Shining");  
         $display ("------------");  
       end  
    end  

**Output Snippet**  

<img width="435" alt="15" src="https://user-images.githubusercontent.com/110443268/188803668-ac46bcff-47a4-4867-8f87-3b946770c3e8.png">

**GitHub Lab Code link**  

**GitHub Lab Output link**  
  


***
### break 

A break statement is used to terminate the loop immediately. When a break statement is encountered inside a loop, the loop iteration stops there. Generally, we use break after giving the condition in code using the if statement.

We can use break statements in any loop(for, foreach, forever, do-while, while, do-while,), for terminating the execution of a loop. It is always used inside the loop. The break statement ends the loop immediately when it is encountered.

**Syntax**:

`break;`

### Example:     
            foreach(array[i])
            if(i==2)begin
            $display("----Calling break----");
            break;
            end

In the above example, a break statement is used inside the loop which terminates the loop when condition is true. In this break is used at index 2 so that the loop stops at index 2 and comes out of the loop.



**Flowchart:**

![Untitled Diagram-Page-1 drawio (5)](https://user-images.githubusercontent.com/110447788/188305065-221831fc-8e53-48dd-b9de-da445a1a4861.png)

                                      Fig-: flow chart: break statement

**Output snippet:**


![Untitled Diagram-Page-3 drawio (1)](https://user-images.githubusercontent.com/110447788/188300378-7daf30b0-062b-47c6-b265-bacb850aa0ed.png)

                          Fig - : Output: break statement gets executed at iteration 2

In the above output, a break statement is used inside the loop. The output shows the value for index 0 & 1, after this break statement is encountered and display "Calling break"



**lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/break/break.sv

**lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/break/break_op.log

### continue:

The continue statement is used to skip the current iteration of a loop. We can use the continue statement inside any type of loops such as for, while, and do-while loop. Basically, continue statements are used in situations when we want to continue the loop but do not want the particular iteration in the loop.

Using continue, we can skip the current iteration of a loop and jumps to the next iteration of the loop immediately

**Syntax**:

`continue;
`
###  Example:   
            foreach(array[i])
            begin
            if(i==2)begin
            $display("-----Calling Continue----");
            continue;
            end

In the above example, **continue** statement is used inside the loop that skips the current iteration of a loop. In the following loop **continue** is used at index 2 so that the loop skips the particular iteration at index 2 and goes for the next iteration.    




**Flowchart:**

![Untitled Diagram-Page-1 drawio (6)](https://user-images.githubusercontent.com/110447788/188305077-aca9f33b-5b5c-4c4c-a674-a262c6c6cf7c.png)

                                        Fig - : flow chart: continue statement

**Output snippet:**

![Untitled Diagram-Page-4 drawio (3)](https://user-images.githubusercontent.com/110447788/188300409-2097d70f-2fc7-4105-9a32-d4fc9c24c9af.png)

                                  Fig - : Output: continue statement executes at iteration 2 

In the above output, the continue statement is used inside the loop. The output shows the value for iterations 0 & 1 and for iteration 2  continue statement is encountered and displays "Calling continue" and after this jumps to the next iteration immediately and prints the value for iterations 3 & 4


**lab link** https://github.com/piyushagrawal4578/control-flow/blob/main/continue/continue.sv

**lab output link** https://github.com/piyushagrawal4578/control-flow/blob/main/continue/continue_sv_op.log




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









 



             
