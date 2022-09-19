# Constraint  
The constraint is the way to assign legal value to the random variables. Constraints help us to limit the randomness of the variable by specifying the range. The way to create valid test configurations is by the use of constraints.  
 
To enable the randomization we use rand() and randc() function. 
For using the constraint first, we need to assign the random variables by using the keyword rand or randc. After that declare the constraint statement.  

All the constraint blocks are active at the same time.   
**Syntax**  
constraint  constraint_name{random_variable[range];}  

**Note**-  If the variable is randomised without any constraints, then any value in the range will be assigned to the variable with equal probability. 
***
  Randomization is done in two ways.  
1. Random function system
2. Random Variables 


***
 

## 1.Random Function system  
This system function is used to give the pseudorandom numbers.  These functions are used inside the "initial begin" block. There are generally two system functions used and these are -
|$urandom()|$random()|$urandom_range()|
|:---------|:---------|:---------------|
|Return 32-bit unsigned random number but the number remains the same throughout the simulation unless we change the seed number. For the particular seed number again the random number is fixed and does not change throughout the simulation.  | Returns 32-bit signed random number and same as $urandom() not change the value throughout the simulation unless the seed number changed  .| Returns the unsigned value for the given specified range and not change value throughout the simulation time.  Syntax - $random(max,min);|

 
**Example -**  
 The below example shows the random function code.   

**Code Snippet**  
  
     a = $random();  
     b = $urandom();  
     c= $urandom_range(4,2); //GIVING RANGE (MAX,MIN)  
     d = $random(23); // assign some seed value  
     e = $urandom(4); // assign seed value  
     $display ("a=$random()      // Return 32 bit signed random variable");  
     $display("Random Value of a  =  %0d",a);    
     $display("b = $urandom()   // Return 32 bit unsigned random value .");    
     $display("Random Value of b = %0d",b);  
     $display ("c = $random_range(4,2)   // Return the unsigned random number") ;    
     $display("                          by giving the range to the variable");  
     $display("Random value of c = %0d",c);  
     $display(" $random(seed);     // assign some seed value, it will display 32 bit ");  
     $display ("                         signed random value for the given seed value ");  
     $display ("d = $random(23);  // Seed value =23");  
     $display ("Random value of d = %0d",d );  
     $display ("$urandom(seed);  // assign the seed value , it will display 32 bit ");  
     $display ("                    unsigned random value for the given seed value ");     
     $display ("e = $urandom(4);  // Seed value = 4;");  
     $display ("Random value of e = %0d", e);  
     end  

**Output Snap**  

<img width="734" alt="cons_1" src="https://user-images.githubusercontent.com/110443268/190629477-ff70f07c-db95-4387-bdff-2b5ba7589cae.png">

**GitHub lab file link**  

**GitHub log file link**  

***

## 2.Random Variables 
Generally, a random variable is a variable whose value is unknown or a function that assigns values to each of an experiment's outcomes. 
The class variables which get random values on randomization are called random variables. The value of the random variable is uniformly distributed for the range. 
 
**Purpose of random variables** 
When we do direct tests, we need some time to think about the possible conditions or scenarios for the test and there is a possibility that we missed some test cases. To solve this random variable concept is introduced.  
In a random variable, random values in that particular assigned range will be generated.  
_The drawback of random functions is, that they cannot change the value throughout the simulation times ._ 


 To use, random variables, class variables need to be declared using the rand and randc type-modifier keywords.  

### rand 
rand is non-cyclic in nature. It will randomly give any value and can repeat the value before completing the cycle.  

**Example**  

The below example is of rand variable.  

**Code Snippet**  

     class rand_function;  
       rand logic [2:0] a ; // byte is 2 state signed data type  
    endclass  
    rand_function raf;  
      module rand_var;  
      initial begin  
      //  rand_function ra_f;  
      raf = new();  
     $display ("rand - Randomizing the value of the variable in non-cycling form  ");  
     for (int i =0;i <= 10;i++)begin  
     void'(raf.randomize ());  
      $display("Iteration = %0d Random value of a = %0d",i, raf.a);  
     end  
    end  
   

**Output Snap**  

<img width="632" alt="cons_2" src="https://user-images.githubusercontent.com/110443268/190632351-751fcc5f-d868-4806-b9dc-0640bdde233e.png">



**GitHub lab code link**  

**GitHub lab output link**

### randc  
randc is random cyclic and cycles through all the values within their range before repeating any particular value.
randc is cyclic in nature. It will give a random value and repeat it after completing the cycle.  

**Example**     

The below example is for randc variable.  
  
**Code Snippet**  

     class pack;  
       randc bit [2:0]a;  
     endclass  
     module randc_var;  
     pack pk=new();  
      initial begin  
       $display (" randc - It  is cyclic in nature . It will repeat ");  

       $display ("         it's value after completing one cycle .");  

      for (int i =0; i<=12;i++)begin  
      void'(pk.randomize ());  
       $display("Iteration =  %0d    Random Value =  %0d ", i ,pk.a);  
     end  
     end  

   
**Output Snap**   

 
<img width="569" alt="cons_3" src="https://user-images.githubusercontent.com/110443268/190633546-3f5186af-d62a-4ab5-9e17-4ec6376bedc3.png">


**GitHub lab code link**   
 
**GitHub log output link**



***
## Constraint Block 
Constraint blocks are the class methods just like function and task. Constraints have unique name in the class.  

**Syntax**  
  
constraint [const_name] {expression 1; expression 2; ... expression N}  
  
Instead of begin end block, constraint blocks are enclosed with curly braces.  
**Conflict in constraint**   
Conflict in constraint blocks are arise when -  
1. We declare more than one constraint with the same name.
2. If there is non-matching in the given ranges of constraint.  

We can declare constraints inside and outside of the class. For declaring the constraint outside the class, use the "extern" keyword.  
   
**Declare the constraint outside the class block**  

![Untitled Diagram drawio (20)](https://user-images.githubusercontent.com/110443268/187884562-6e352c45-615b-4932-93d1-46d00eec0285.png)

If we declare constraint without using the extern keyword, then it will display a warning while compiling.  
  
**Example**  

The below example will show the constraint declaration with the use of the extern keyword.  

**Code Snippet**  

    class class_a;  
     rand byte a;  
     rand byte x;  
     constraint b{a<6;  
                  a>2;}  
     extern constraint y;  
     endclass  
     constraint class_a:: y{x>7;}  
     module mod;  
     class_a pack;  
     initial begin  
      pack = new;  
      for (int i =0;i<=5;i++)begin  
       void'(pack.randomize());  
       $display ( "Iteration = %0d  Value of a = %0d Value of b = %0d  " , i,pack.a,pack.x);  
      end  
      end  

**Output Snap**  

<img width="554" alt="cons_4" src="https://user-images.githubusercontent.com/110443268/190843316-09b3ad9c-88fd-445c-916a-5b7c74d4e074.png">



**GitHub Lab file link**  
 
**GitHub Lab Output link**-


***
## Array Randomization  
Randomization can also be done in array data types like static array, dynamic array and queues. The variables have to be declared with the type rand or randc to enable the randomization of the variable.  


### Static array randomization 
  
In a static array, randomization is possible only for the array elements. As the size is fixed, it is not possible to change it.  
Declare the array as the keyword rand or randc and on randomization, the elements of the array will get random values.

**Example**-  
The below example show the randomization of the one-dimensional static array.  

**Code Snippet**   

     class static_array;  
      randc byte  a[5];  
     endclass  
     module stat_array;  
     static_array stat_arr;  
     initial begin  
     stat_arr = new();  
     $display ("Static array - Size is already declared. So, we can only randomize ");  

     $display ("               the elements of it . ");  
     $display ("rand byte a[5];  // Data type is byte");  
     $display ("Before randomize the elements of array 'a'");  
     $display ("Assign by the default value of array data type.");  
     $display (" %0p", stat_arr.a);  
     void '(stat_arr.randomize ());  
     $display ("After randomize the elements of array 'a'");  
     $display ("Output =  %0p ",stat_arr.a);   
     end  
     

  

**Output Snap**   

<img width="671" alt="cons_5" src="https://user-images.githubusercontent.com/110443268/190843990-17077350-b02a-4c75-8299-4580f5681380.png">

 

**GitHub lab code link**  

**GitHub lab output link**  

**Example -2**-  
The below example shows the randomization of a two-dimensional static array.  

**Code Snippet**  

    class class_1;  
     rand bit [3:0]a[2][4];  
    endclass  
    module mod;  
    class_1 pack;  
    initial begin  
     pack = new;  
    $display ("The value elements of array before randomization = %0p",pack.a);  
     for (int i =0;i<=5;i++)begin  
     void'(pack.randomize());  
    $display ("The value of elements of array after randomization = %0p",pack.a);  
    end
    end   


**Output Snap**  

<img width="872" alt="cons_8" src="https://user-images.githubusercontent.com/110443268/190866664-ad77e697-fed4-476d-b0e8-033171262c8c.png">


**GitHub Lab File Link**  

**GitHub Lab Output Link**  
  


### Dynamic Array  
A dynamic array has no predefined size during array declaration. Generally, the array_name.new() keyword is used to assign the size of the dynamic array.  
Constraints are used in two ways -    
1. To limit the size of the dynamic array by using the keyword size in the constraint block.  
2. To give the value using operators for the elements of the dynamic array using "foreach" conditional statement in the constraint block.     
The below example will show how to randomize the dynamic array.

The output after randomization is an empty array if the size is not constrained.  

**Example**-    
  

**Code Snippet**  

    class class_1;  
     randc bit [7:0] dyn_arr[];  
     // declaring a dynamic array, each element is of 7 bits.  
     constraint dyn_arr_size{dyn_arr.size()>3;dyn_arr.size()<7;}  
     // declare the size of the dyn_arr between 3 to  
     //int i =4;  
     constraint dyn_arr_ele{foreach (dyn_arr[i])   // each element value is square of the index number.  
                            dyn_arr[i]==i*i;}  
     endclass  
     module mod;  
     class_1 pack;  
     initial begin  
     pack = new();  
     //$display ($size(pack.dyn_arr);  
     void'(pack.randomize());  
     for (int i = 0;i<pack.dyn_arr.size();i++)begin  
     $display ("Iteration =%0p Value =%0p",i,pack.dyn_arr[i]);  
     end  
     end  


**Output Snap**  

<img width="654" alt="cons_7" src="https://user-images.githubusercontent.com/110443268/190845175-40912616-514a-42e2-942f-9bd099bc3b6b.png">

 
**Lab link**

**log file link**  

### Queue  
Queue size will get randomized based on size constraints, and queue elements will get random values.  
The below example will show, how to randomize the elements of the queue.  
**Output snap**  
**lab link**  
**output log file link**  




   





 


## 