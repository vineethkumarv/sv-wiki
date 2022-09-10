# Functions

The main usage of a function is to write a piece of code that can be called at any time and n number of times by simply calling the function name which doesn't take any simulation time to execute.  
Functions are return type that will return **only** a single value mentioned in the function declaration, if not mentioned then return a one-bit value  

syntax :  
`initial`  
`begin`  
`function_name(arguments);`  
`end`  

`function return_type function_name(arguments);`  
`statement1;`  
`statement2;`  
`.`  
`.`  
`statementN;`  
`endfunction`  

**limitations:**  
* The code inside the functions is not allowed to have time-consuming statements like #, @, wait
* can only return one value
* cannot call a task from the function as the task is allowed to have time-consuming statements

There are a lot of variations to call a function  

* [Calling a function with values as arguments](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-values-as-arguments)   
* [Calling a function with variables as arguments](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-variables-as-arguments)   
* [Calling a function with values from an expression](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-values-from-an-expression) 
* [Calling a function with variables with positional arguments](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-variables-with-positional-arguments)  
* [calling an automatic function](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-an-automatic-function)  
* [calling a function with variables with reference of variables](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-variables-with-reference-of-variables)   
* [calling a function with a void return type](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-a-void-return-type)   
* [calling a function with return an array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-with-return-an-array)  
* [calling a function from an expression that returns an array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-function-from-an-expression-that-returns-an-array)      
* [Calling a task from function(exceptional case by using fork and join_none)](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Functions#calling-a-task-from-a-function)  


## Calling a function with values as arguments

**Example:**  

          int result;  
          initial  
          begin  
          result=sum(5,6);  
          $display("\treturned from function and");  
          $display("\tstored the value of sum in result");    
          $display("\n\t@ %0t ns, value of sum is %0d",$time,result);     
          end  
          function int sum(int var1,var2);    
          $display("entered into function");   
          return var1+var2;  
          endfunction   

Here in the above example function name is sum which is of return type int i.e., it has return a one int value only.  

**Flowchart:**

![function flowchart - Copy](https://user-images.githubusercontent.com/110412468/188573070-fc9e6eef-762a-44a5-8adf-3957dbbeaf91.png)   

                    Flowchart.1- functions passing values  

**output:**  

![func pass by val1](https://user-images.githubusercontent.com/110412468/188588577-c1aef74b-1d62-4b46-adb3-7b43662f042b.png)  

              Fig.1- output for function with passing values as arguments  

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_val/func_pass_by_val.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_val/func_pass_by_val_log.log  

In the above example, the result is a variable declared as int to store the result of the function sum.  
when the sum function is executed, the simulator checks for the function named sum is present or not, if yes then compares the arguments and return the type of function if all match then it proceeds with statements of the function. Then the value 5 is stored in var1, and 6 is stored in var2 After entering into the function it will display entered into function, and next, it will return the value of var1+var2 which will be caught by the variable result and displayed in the next line.

## Calling a function with variables as arguments   

**Example:**  

          int result,a=5,b=6;    
          initial  
          begin  
          $display("\tcalling the function");  
          result=sum(a,b);  
          $display("\treturned from function and");  
          $display("\tstored the value of sum in result");  
          $display("\n\t@ %0t ns, value of sum is %0d",$time,result);    
          end  
          function int sum(input int a,b);  
          $display("entered into function");   
          return a+b;  
          endfunction  
 
**Flowchart:**  

![function flowchart - Copy (2)](https://user-images.githubusercontent.com/110412468/188593202-c0bb5016-f856-4a55-ba94-0d45826642db.png)  

                    Flowchart.2- functions passing arguments as variables   

**output:**  

![func pass by variables1](https://user-images.githubusercontent.com/110412468/188593334-04c163c0-df7c-4ddf-9dc0-832bf29a9bad.png)  

              Fig.2- output for function with passing values as variables  

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_variables/func_pass_by_variables.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_variables/func_pass_by_variables_log.log  

This is almost similar to the example of passing by values but here will just pass the values by storing the values in variables so that the same line can be reusable if needed and here the variables called in initial module a&b are different than the a&b in function i.e., they have separate memory if any change is made in function on variables a&b then it won't be reflected with values of main modules a&b until a&b are declared as global. 
Here in the functional declaration we also mentioned input for variables whereas in the first example we didn't mention it, so we can give the directions of arguments if necessary and only one output is possible for functions.

## Calling a function with values from an expression  

**Example:**   

          initial  
          begin   
          $display("\n\t@ %0t ns, value of sum is %0d",$time,sum(5,6));    
          end  
          function int sum(int var1,var2);  
          $display("entered into function");   
          return var1+var2;  
          endfunction  

**output:**  

![func call from display1](https://user-images.githubusercontent.com/110412468/188594048-7d9f5443-493d-4b26-805c-9e3e5f9c897d.png)    
   
              Fig.3- output for function call from an expression    

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_call_from_display/func_call_from_display.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_call_from_display/func_call_from_display_log.log  

In the above example, we didn't use any variables to store the values of the return type of the function, function is called directly from the display statement where the return value is passed to the display statement or else can be used in any expression i.e., function can be called as part of an expression (if we want to add 3 values of 4,5,6 then we can use as 4+sum(5,6).)  

## Calling a function with variables with positional arguments  

**Example:**   

          initial  
          begin   
          result=sum(.var1(5),.var2(6));  
          $display("\treturned from function and");  
          $display("\tstored the value of sum in result");  
          $display("\n\t@ %0t ns, value of sum is %0d",$time,result);      
          end  
          function int sum(int var1,var2); 
          $display("entered into function");   
          return var1+var2;  
          endfunction  

**output:**  
  
![func pass by positional1](https://user-images.githubusercontent.com/110412468/188599306-fc055066-b27a-4c07-8159-ea5ee63d940f.png)  
   
              Fig.4- output for function call passing positional arguments   

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_positonal/func_pass_by_positional.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_positonal/func_pass_by_positional_log.log  

In the above example, we are calling the function using positional arguments i.e., value 5 is pointed to var1 of the function and 6 to var2 and then after works as a normal function only.

## calling an automatic function  

**syntax:**  
`function automatic function_name(arguments);`  

**Example:**  

          module func_automatic();
              int result1,result2;
              function int factorial_static(int var1);
              if(var1>=2)
                result1=factorial_static(var1-1)*var1;
              else
                begin
                  result1=1;
                end
                return result1;
              endfunction
  
              function automatic int factorial_automatic(int var1);
                if(var1>=2)
                  result2=factorial_automatic(var1-1)*var1;
                else
                begin
                  result2=1;
                end
                return result2;
              endfunction
            initial
            begin
              
                result1=factorial_static(5);
                result2=factorial_automatic(5);
              
              $display("factorial_static:%0d",result1);
              $display("factorial_automatic:%0d",result2);
            end
          endmodule: func_automatic  

Here we are using the function with an automatic keyword which means whenever the function is called the new memory is created whereas in static the same memory is used whenever the function is called.   

**output:**  
  
![func fact static automatic](https://user-images.githubusercontent.com/110412468/189047517-291148e2-d4df-4a37-8af4-4e3585c085dd.png)
     
              Fig.5- output for automatic function     

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_automatic/func_automatic.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_automatic/func_automatic_log.log  

In the above example, we created two functions one is static & other is automatic and calling the sum function twice in the fork so runs parallel and runs concurrently so in the static function the previous memory is overwritten with the old values so that's why lost the data of sum which is 5 but in automatic, it was showing as expected, so whenever automatic is used new memory is allocated for every call.  


## calling a function with variables with reference of variables  

**syntax:**  
`function automatic data_type function_name(ref arguments);`    

**Flowchart:**  

![function flowchart - Copy (3)](https://user-images.githubusercontent.com/110412468/188602682-44e19404-dd9e-451a-a83d-6f317841550e.png)

                    Flowchart.3- functions passing arguments as variables with reference  
**Example:**   

          int result,addend,augend;  
          initial  
          begin   
          addend=5;  
          augend=6;  
          $display("\tBefore calling function -> addend = %0d , augend = %0d",addend,augend);  
          $display("\tcalling the functions");  
          result=sum_without_ref(addend,augend);  
          $display("\tafter calling function without ref -> addend = %0d, augend =%0d",addend,augend);  
          result=sum_with_ref(addend,augend);  
          $display("\tafter calling function with ref -> addend = %0d, augend =%0d",addend,augend);  
          end  
          function automatic int sum_with_ref(ref int var1,var2);  
          int temp;  
          $display("\n\tentered into with ref function");  
          temp=var1;  
          var1=var2;  
          var2=temp;  
          $display("\tswapped variables by using ref ");  
          return var1+var2;  
          endfunction : sum_with_ref  

          function int sum_without_ref(input int var1,var2);  
          int temp;  
          $display("\n\tentered into without ref function");  
          temp=var1;  
          var1=var2;  
          var2=temp;  
          $display("\tswapped variables by without using ref ");  
          return var1+var2;  
          endfunction : sum_without_ref  

when calling the function by passing variables reference, need to mention the keywords automatic and as well as ref for the arguments as shown in the above example.  

**output:**  
  
![func pass by ref1](https://user-images.githubusercontent.com/110412468/188600795-1c972676-f695-4f83-8fcf-b2567a85cd43.png)  
   
              Fig.6- output for function call passing arguments with reference   

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_ref/func_pass_by_ref.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_pass_by_ref/func_pass_by_ref_log.log  

In the above example, here trying to call the function by passing the variables reference which means the values addend and augend in the main module and in the automatic function both share the same space of memory. In the example mentioned both static and automatic were given the sum and swapped the variables which are performed in automatic but not in static function.   
 
## calling a function with a void return type  

**syntax:**  
//type casting  
`void'(function_name(arguments));`  
 or  
//declaring the function as void type which doesn't return any value.   
`function void function_name(arguments);`  

**Example:**  

          initial  
          begin  
          (display("\t ----output for function void return type-----");  
          (display("\t passing string to function for displaying");  
          end  
          function void display(string str);  
          $display("%s",str);    
          endfunction: display  

**output:**   

![func return void1](https://user-images.githubusercontent.com/110412468/188607672-a724034e-477d-4467-aa18-08e57e5c74be.png)
   
              Fig.7- output for void function type     

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_return_void/func_return_void.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_return_void/func_return_void_log.log  

In the example, we are calling the function but don't care about the return value of the function, but if we don't mention then the compiler will through warning so in that case will use the convert the function data type to void or else can ignore at function calling point by using the type conversion 

## calling a function with return an array

**syntax:**  
`int array_name[size];`  
`function function_name(array_name);`  

**Example:**  

          int array[5];  
          void'(fun_arr(array));  
          $display("\treturned from function");  
          $display("\n\t@ %0t ns, Array elements = %0p",$time,array);  
          end  
          function automatic int fun_arr(ref int arr[5]);  
          $display("\tEntered the function");  
          foreach(arr[i])begin  
          arr[i]=i+1;  
          end  
          $display("\t values assigned to array elements starts from 1");  
          return arr[5];  
          endfunction  

**output:**  

![func return arr1](https://user-images.githubusercontent.com/110412468/188604840-93f11301-2bff-48e8-b54e-cee307a35de9.png)  
   
              Fig.8- output for function returns an array     

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_return_arr/func_return_arr.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_return_arr/func_return_arr_log.log  

In this example, calling the function with an array, initially took an empty array of int type so will have all 0's initially and in function assigning the values starting from 1 and incrementing by 1 value and assigning for each index of the array with help of foreach loop, here we used reference so the arr and array both are same. 


## Calling a function from an expression that returns an array

**Example:**  

          typedef int array[5];  
          array array_hndl;  
          initial  
          begin  
          $display("\n\t@ %0t ns, Array elements = %0p",$time,fun_arr(array_hndl));  

          function array fun_arr(int arr[5]);  
          $display("\tEntered into the function");  
          foreach(arr[i])begin  
          arr[i]=i+1;  
          end
          $display("\tvalues assigned to array elements starts from 1");  
          array_hndl=arr;  
          return array_hndl;  
          endfunction  

**output:**   

![func array from display1](https://user-images.githubusercontent.com/110412468/188615368-51613153-5cc7-4698-820e-e22fe12e0d43.png)  
   
              Fig.9- output for a function call from an expression that returns array    

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_array_from_display/func_array_from_display.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/func_array_from_display/func_array_from_display_log.log  

In the example, we are calling a function from a display that returns an array where we need to create a data type using a typedef as mentioned in code with the array and size and make use of that data type and call the function, note that you need to change the function return type to the typedef type.

If using a normal array and trying to call the function from an expression, then the function will return only 0 as one value, not even an array, and shows as follows.   

![err](https://user-images.githubusercontent.com/110412468/188617693-4cf80a27-c8fe-4437-8f85-35ec9c6665da.PNG)  

## Calling a task from a function  

In general, calling a task from a function is illegal, the compiler will through an array but there is an exceptional case for that, the task can be called from a function by using a fork join_none as sown in the following example.

**Example:**  

          initial  
          begin
          $display("\t@ %0t ns, In the initial block",$time);  
          $display("\tcalling function");  
          #1 void'(function_call);  
          end  

          function function_call;  
          fork  
          $display( "\t@ %0t ns I'm in function",$time);  
          $display("\t@ %0t ns, calling task from func",$time);  
          task_call;  
          join_none  
          endfunction  

          task task_call;  
          #1 $display( "\t@ %0t ns , I'm in task",$time);  
          #1 $display("\t@ %0t ns,leaving from task",$time);  
          endtask  


**Flowchart:**  

![task from func](https://user-images.githubusercontent.com/110412468/188619777-ff448c85-170e-4604-a466-779d621944c3.png)

                    Flowchart.4- calling a task from the function  

**output:**   
 
![task from func1](https://user-images.githubusercontent.com/110412468/188620923-5148ad27-001e-496a-8c10-918cf0c93e65.png)
   
              Fig.10- output for calling a task from function      
              
**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/task_from_func/task_from_func.sv  
**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_Team_SiliconCrew/functions/task_from_func/task_from_func_log.log  

In the initial block, called a function that has some statements and calls a task inside the fork join_none so that the task from a function can be accomplished, here at 0 ns the simulator is in the initial block and a func is called, then @1 ns it printed that I'm in function and task is called @1ns in func and from there simulator goes to task, @2ns it prints I'm in task and waits for 1ns more and leaving the task.
