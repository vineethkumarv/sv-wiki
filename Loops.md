# Loops
A Loop is nothing but statements that need to be run more than once are included in the loop instead of writing the statements repeatedly. Loops will run multiple times based on conditional statements, If the condition is always true then it becomes an infinite loop and the system will hang.  

**loops fig**  

## loops cheat sheet
|S.No.|Loops_variants|Explanation|
|:----|:-------------|:----------|
|1.|[while]()|Repeats the set of statements based on condition|
|2.|[do_while]()|Once runs the statements without checking the condition then behaves as while|
|3.|[repeat]()|Repeats the statements only a particular number of times|
|4.|[for_loop](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Loops#4for-loop)|Similar to while but more compact than while|
|5.|[foreach](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Loops#5foreach)|Only Used to traverse through every element of array |
|6.|[forever](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Loops#6forever)|Repeats the statements throughout simulation|  
 
***
## 4.for loop  

For loop is simply a more compact form of while loop. In for loop assignment, there are three parts:  
* Initialization - initialize the required variables for running the loop.
* condition  - based on this condition the number of repetitions of for loop is dependent.
* modifier - incrementing/decrementing the variables.

**Syntax:**  
`for ( Initialization ; condition ; modifier )`  
`begin`  
`statement1;`  
`statement2`  
`.`   
`.`  
`statementN;`  
`end`    

**Example:**  
`for (int i=1;i<=5;i++)`  
`begin`   
`$display(" Iteration %0d ",i);`   
`end`  
`$display(" out of loop ");`

 In the above example, i is the variable initialized and declared as 1, here i is the local scope only means we can't use i out of for loop. In condition i should be less than or equal to 5 means for loop statements will be executed if the value of i is matched with condition or else comes out of the loop and the last part is the modifier which is incrementing i value by 1.  

**Flowchart:**  

![forloop](https://user-images.githubusercontent.com/110412468/188261911-62cacd1a-ee35-427a-8247-27f25a6fef28.png)  

               Flowchart.1 - for loop flowchart  

**output:**  
![for1](https://user-images.githubusercontent.com/110412468/188284411-8bbf4704-d0a5-4f19-8ad3-9dc068d30d31.png)  

         Fig.1 - for loop output

As per the flowchart initially, i is 1 so the condition satisfies and performs display statement and prints as "iteration 1" and then goes to modifier and increments i, check the condition again and so on till i=5, now after 5 i is incremented to 6 then checks condition which is failed so comes out of the loop.

**Github lab code link:**  
**Github lab output link:**   

Note: If you use a local scope variable outside then the compiler throughs an error as shown below.

![for error1](https://user-images.githubusercontent.com/110412468/188284390-190b7e96-887b-4234-9aaa-56303b6afc80.png)

         Fig.2 - error of for loop local scope variable usage out of loop


***

### Nested for loop

**Syntax:**  
`for ( Initialization ; condition ; modifier )`    
`begin`  
`statements;`
`for ( Initialization ; condition ; modifier )`
`begin`  
`statements;`
`end`   
`end`  

**Example:**   

`for (int i=1;i<=2;i++)`  
`begin`  
`$display("\n\t%0d Table:\n",i);`  
`for(int j=1,k=0;j<=10;j++)`   
`begin`  
`k=i*j;`  
`$display("\t %0d X %0d = %0d",i,j,k);`  
`end`  
`end`  

In the above example we are using nested for loop to print tables, so took i as table number and j for going from 1-10 and k to store the value of multiplication. Here observe that j & k are used at the same initialization and you can do the same for conditions and modifiers also to have multi variables at a time.

**output:**  
![table loop1](https://user-images.githubusercontent.com/110412468/188284380-5c87ad4b-8990-4abd-bea0-177beefece59.png)    

         Fig.3 - nested for loop output  

In this i,j& k are used as i X j = k, so i is range from 1-2 and each has j from 1-10 and k is storing and printing using display statements.    

**Github lab code link:**    
**Github lab output link:**    

**Advantages:**
* Readable
* syntax will be easier(can mention all initialization,condition, modifier in a single place)  

**limitations:**  
* variables initialized are only local.  

***
## 5.foreach 

This loop is an upgraded version of for loop for traversing through each element of an array. This iterates through index 0 till the size of an array mentioned.

foreach is a shorter version of the following for loop  
`for(int i=0;i<$size(array);i++)`


**Syntax:**  
`foreach(array[i])`  
`begin`  
`statement1;`  
`statement2`  
`.`   
`.`  
`statementN;`  
`end`    

**Example:**  
`int array[5]`  
`foreach(array[i])`    
`begin`     
`array[i]=i;`   
`$display("\tarray[%0d]=%0d",i,array[i]);`    
`end`    
`$display(" out of loop ");`  

In the above example, a fixed array of size 5 is taken, using a foreach loop to traverse through each element, and executes the statements of the foreach loop from array[0] to array[4].  
  

**Flowchart:**  

![foreach flowchart](https://user-images.githubusercontent.com/110412468/188263683-d16a12a4-b6a5-4dc5-aa13-20cade36fd31.PNG)  

               Flowchart-2.foreach loop flowchart  

**output:**  
![foreach1](https://user-images.githubusercontent.com/110412468/188284453-97501f0b-3bd3-4231-bc70-2bb179409464.png)   

         Fig.4 - foreach loop output  

As per the flowchart initially checks for the size of the array, as it is >0, so proceeds to execution of foreach statements i.e., assigns array[0]=0 and displaying the same and then increments i value by 1 and repeats the same until array[4]. Then at array[5] condition is failing because the array size is 5 only (i.e., 0,1,2,3,4) comes out of loop.

**Github lab code link:**  
**Github lab output link:**   

The same functionality of above program we can achieve by using for loop as following line replaced with foreach.  

`for(int i=0;i<$size(array);i++)`  

The following is the snap of output of foreach using for loop
**output of foreach using for loop:**  
![foreach using for 1](https://user-images.githubusercontent.com/110412468/188284443-a376de17-b164-427e-98f4-659f6c6a2ccc.png)  

         Fig.5 - foreach using for output

**Github lab code link:**   
**Github lab output link:**  

**Note:** we can use nested foreach similarly as used in nested for loop and can access multidimensional arrays.  

**Advantages:**  
* syntax is easier.
* Readable
**limitations:**  

* It is only used for arrays  
* Modifier is not accessible(if we want to store array only in even positions then foreach not good option) 
* Cannot traverse through array in reverse fashion  
  
***
## 6.forever  

The forever loop name itself says that it will run forever i.e., throughout the simulation or forcefully shut down the forever loop.  
It is similar to the always procedural block in System Verilog but generally, it's not possible to use always in classes to achieve that concept we can make use of this forever loop.  
If we use a forever loop without force stop the compiler will hang.
There are two ways to stop forever, they are   
* $finish;
* break;

* ### forever with $finish:
forever loop doesn't have any conditions as the number of times to repeat the loop is infinite so no condition is needed.
**Syntax:**  
`forever`  
`begin`  
`statement1;`  
`statement2`  
`.`   
`.`  
`statementN;`  
`end`    

**Example:**  
`forever`  
`begin`   
`$display("\t @ %0d ns Iteration %0d",$time,a);`  
`a++;`  
`#4;`  
`end`  
`initial begin`  
`#20 $display("\n\t@ %0d ns Stopped using $finish",$time);`  
`$finish;`  
`end`  
  
In the above example, forever is used which is having display statement and increment a and a 4ns delay for every repetition like that it will run forever but in another initial block there is $finish which will stop the simulation so this stops the forever also.


**Flowchart:**  
  
![forever finish](https://user-images.githubusercontent.com/110412468/188265756-3184f9c5-fc3e-4597-b10b-b096416f339a.png)  

               Flowchart-3.forever with finish flowchart  

**output:**   
![forever using finish1](https://user-images.githubusercontent.com/110412468/188284468-0ab76b2c-abde-49f4-84dc-5c603adfcf3d.PNG)  

         Fig.6 - forever with finish output  

As the forever doesn't have any condition it simply enters and displays a value and then a is incremented and a 4ns delay is introduced so for every 4ns the output is getting printed and at 20 ns $display and prints stopped using $finish is executed in second initial module as well as $finish is called in which will terminate the simulation.

**Github lab code link:**  
**Github lab output link:**   

* ### forever with break:  

**Syntax:**  
`forever`  
`begin`  
`statement1;`  
`statement2`  
`.`   
`.`  
`statementN;`  
`end`    

**Example:**  
`forever`  
`begin`  
`$display("\t @ %0d ns Iteration %0d",$time,a);`  
`a++;`  
`#4;`  
`if(a>8)`  
`break;`  
`end`   
`$display("\n\t@ %0d ns Stopped using break",$time);`   
`end`  
  
This is similar example of forever with $finish but here we have used break condition instead of $finish based on a value greater than 8.


**Flowchart:**  
  
![forever break](https://user-images.githubusercontent.com/110412468/188266175-5b081e46-62ac-4be8-8dd6-9bbf11e397d5.png)

               Flowchart-4.forever using break flowchart  

**output:**  
![forever using break1](https://user-images.githubusercontent.com/110412468/188284478-a5724ff5-5b7f-445c-b36b-309dbd386c68.PNG)    

         Fig.7 - forever with finish output  

As the forever doesn't have any condition it simply enters and displays a value and then a is incremented and a 4ns delay is introduced so for every 4ns the output is getting printed after a value greater than 8 then enters into if block which has a break which moves simulator to out of the loop.

**Github lab code link:**  
**Github lab output link:**   

**advantages:**  
* we cant use always block inside an always or a class there this forever is used and can achieve the same job  
**limitations:**  
* If we don't quit the forever then the simulator will hang.

***