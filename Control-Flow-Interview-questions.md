
1.**How to call the function inside a task? giving example with code.**

**Answer**: Normally task can be a call function inside the task.    
but calling the task inside the function is not possible because task has delay elements and the function does not have any delay elements but a wall clock delay is there.      
using the fork and join_none in inside the function to call the task is possible.  

Please refer to the below code for a better understanding.  
 
             module test;  
             initial begin  
             void'(function_sum);  
             end  
   
             function function_sum;    
             $display($time, "\t function");   
             fork 
             task_sum;
             join_none
             endfunction  

             task task_sum;    
             # 5 $display($time,"\t task");   
             endtask  

             endmodule  

 The below figure shows the output of calling a function inside a task.  
![Untitled Diagram drawio (9)](https://user-images.githubusercontent.com/106074838/188474636-7609f629-5713-46ff-bfbd-c9753fd06b99.png)  

                      Figure.1. output of calling a function inside a task. 

The above screenshot is telling calling a task inside a function. 
In the inside function, we call the task by using the fork-join_none process.  

***
   



2.**What is the output of x= 2 using a repeat loop?**  

**Answer**:In the repeat loop is used for repeating statements or operations for a fixed number of times.    
but here initially they give the value and value is 2     
Statements will be repeated 2 times and 2 values will be incremented to 3.     

Please refer to the below code for a better understanding.  

                    module test;    
                    int x=2;      
                    initial begin      
                    $display("output of repeat(x=2) is ");     
                    repeat(x)     
                    begin    
                    $display("The value of x is %0d", x);   
                    x++;  
                   end    
                   end  
 
                   endmodule   

The below figure shows the output of the Repeat loop.  
![Untitled Diagram drawio (4)](https://user-images.githubusercontent.com/106074838/188260448-466387c0-54b6-4767-b421-9bb4b83d0a9e.png)   

                          Figure.2. the output of the Repeat loop. 
***


3.**What is dead code in System Verilog?**  
**Answer**: Dead code is code that doesn't affect your simulation or synthesis.   
Examples of dead code are signals that are never used or conditions that are never triggered in code.  

For better understanding follow this link   

***

  
4.**In the Foreach loop can we use a local variable in an inside module? by using the scope resolution operator?**  
**Answer** : No  

                        int array[5]  
                        foreach(array[i])  
                        begin  
                        array[i]=i;  
                        $display("\tarray[%0d]=%0d",i,array[i]);  
                        end  
                        $display(" out of loop ");  

in the foreach loop we use i as a variable and i variable is cant used in the inside module because i refer to the only foreach block itself. not the entire module. and using the scope resolution operator is also not possible.  

***


5.**How to use the forever loop using for loop condition manner**?   
Normally As the name says forever loop will execute the statements inside the loop forever.  
It can be said an indefinite iteration.  
There are 2 ways to do the forever loop in for loop.  
1. using if conditions and break statements inside the for a loop.  
2. $finish.

* **using if conditions and break statements to terminate the loop**    
 
                        module forever_for;  
                        initial begin  
                        $display("-----forever loop output ---");  
                        for (int i=0;1;i++)  
                        begin  
                        #4  $display("\t value of i = %0d", i);  
                        if(i==5)  
                        break;  
                        end 
                        end    
                        endmodule    

In the above code we use the for loop syntax to do the forever loop and inside the for loop **i=0;1;i++** The 2nd condition is 1 which means increment by 1 each time.   
and terminate forever loop by using the if condition and break statements in if conditions we mention i=5 then break it will work 0 to 5 then exits the loop.  



for better understanding go through the below output screenshot (fig number is )    

* **using $finish to terminate the forever loop**  

                  module forever_for;`  
                 initial begin  
                 $display("-----forever loop output ---");  
                 for (int i=0;1;i++)    
                 begin  
                 #4  $display("\t value of i = %0d", i);    
                 end   
                 end  
                 initial begin   
                 #21 $finish;  
                 end    
                 endmodule 

In the above code we use the for loop syntax to do the forever loop and inside the for loop **i=0;1;i++** The 2nd condition is 1 which means increment by 1 each time.  
and terminate the forever loop by using a $finish statement. otherwise, it was an endless loop.    

The below figure shows the output of the forever loop   
![Untitled Diagram drawio (6)](https://user-images.githubusercontent.com/106074838/188388444-a9060788-1faa-4cf9-b4b8-796d41bb6c70.png)  
   
                          Figure.3. the output of the forever loop.  

***
  
 
6.**What is difference between ++i and i++ in SV** ?  
**Answer** :   
++i pre-increment will increment the value of i and then return the incremented value.  

i++ post increment will increment the value of i, Return the original value that i held before being incremented.  

for a better understanding look at the below code   
* pre-increment code
 
                module post_pre; 
                int i=1;  
                int j;  
                initial begin  
                $display("\t the value of i is %0d",i);  
                $display("\t the value of j is %0d",j);  
                $display("\t assigning i value to j");  
                j=++i;  
                $display("\t after pre-increment the value j is %0d",j);  
                end  
                endmodule     
 
In the above code is pre-increment code, i value initially 1 and we assigning i value to j with parallelly doing pre-increment (++i) and assign to j.   

* post increment code  

                module post_pre;  
                int i=1;  
                int j;  
                initial begin  
                $display("\t the value of i is %0d",i);  
                $display("\t the value of j is %0d",j);  
                $display("\t assigning i value to j");  
                j=i++;  
                $display("\t after post-increment the value j is %0d",j);  
                end    
                endmodule  
In the above code is post-increment code, the i value is initially 1 and we assign i value to j with parallelly doing post-increment (i++) and assign to j.  but post-increment values are not updated to the variable j.  

The below figure shows the output of both pre-increment and post-increment 
![Untitled Diagram drawio (7)](https://user-images.githubusercontent.com/106074838/188421237-1af9c422-9c64-4503-a679-e8677f4c0e7d.png)  

                     Figure.4. the output of both pre-increment and post-increment.  
  

*** 

7. Does the Repeat loop inside the break keyword work?  
**Answer** :  
  we use the break keyword inside the repeat loop it will terminate the loop. and based on certain conditions.   

for a better understanding look at the below code  

          module repeat_break;  
          int b;  
          initial begin  
          repeat(5) begin   
          $display("\tVlaue of b=%0d",b);  
          b++;  
          if(b==3)  
          break;  
          end 
          end    
          endmodule 


In the above code is repeat loop with break keyword, we are declaring the repeat loop it will be executed 5 times but using the break keyword to terminate the loop in a 3rd execution time cycle itself.  
       
The below figure shows the output of the repeat loop with the break keyword.   
![Untitled Diagram drawio (8)](https://user-images.githubusercontent.com/106074838/188438380-83f8c068-78f3-491d-9dec-3c1c5febf12c.png)   

                                Figure.5. the output of the repeat loop with the break keyword. 


8.**what is the difference between If and unique if statements**?    
Answer :  
|SL.No|condition | if |unique if |
|-----|----------|----|----------|
|1.|only one conditional expression is true|execute the set of statements inside the true conditional block|execute the set of statements inside the true conditional block|  
|2.|more than one conditional expression is true|executes the first true conditional block statements, no warning display|executes the first true conditional block statements, a warning display|
|3.|none of the conditional expressions is true without else|execute the statements out from the conditional block, no warning display|execute the statements out from the conditional block, a warning display|  



***

9.**what is the difference between If and priority if statements**?  
Answer :  
|SL.No|condition | if |priority if |
|-----|----------|----|----------|
|1.|only one conditional expression is true|execute the set of statements inside the true conditional block|execute the set of statements inside the true conditional block|  
|2.|more than one conditional expression is true|executes the first true conditional block statements, no warning display|executes the first true conditional block statements, no warning display|
|3.|none of the conditional expressions is true without else|execute the statements out from the conditional block, no warning display|execute the statements out from the conditional block, a warning display|  
 

   




  


   






 












