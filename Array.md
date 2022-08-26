# Queue
 Queue is a datatype used to have the variable size ordered collection of same datatypes in unpacked array format, it is used to insert the element in the array and delete the element in the array by both the ends.It is like buffer, used to model the first in first out(FIFO) and last in fast out (LIFO).

****Syntax****: `data_type name[$];`
                 
data_type- data_type of queue element  
name - name of the queue  
[$] - declare the unbounded queue  

There are two types of queue declaration

## 1. bounded

 The queue as the size limit. we need to provide the max value while declare the queue 
 
syntax: `data_type name[$:255];`
 
Here $- first element
255 - last element

![bounded queue](https://user-images.githubusercontent.com/110412474/186423427-f222976c-7179-40ac-83fb-0ae011222e72.jpg)

                            Fig.1: Bounded queue with push and pop operation



---


## 2. unbounded

 The queue as no size limit. we do not provide an size of queue it is a variable size queue.
 
syntax: `data_type name[1:$];`
     
Here 1 - first element
$ - last element


![unbounded queue](https://user-images.githubusercontent.com/110412474/186423948-b22286aa-8de7-4dde-9b0e-08bbdf394306.jpg)

                            Fig.2: Unbounded queue with push and pop operation                         

---  


****Queue method cheat sheet****
Method | Description
-- | --
size() |  returns the number of items in the queue
insert() | inserts the given item at the specified index position
delete() | deletes the item at the specified index position
push_front() | inserts the given element at the front of the queue
push_back() | inserts the given element at the end of the queue
pop_front() | removes and returns the first element of the queue
pop_back() | removes and returns the last element of the queue
  
                    Table.1 Queue Methods
---

## Queue Methods

Example.1 : consider the variable size queue named as queue1 = {2,7,1,9,9,7}, the output is shown in Fig.1
   
* ****size():****

Display the number of element in the queue ,if the queue is empty display the empty array.  
Expression: queue1.size()- It is used to display the size of the array queue1.   
output : 6  

* ****delete():****  
  
It is used to delete the queue element of specified index position.  
Expression : queue.delete(0) - It delete the array element '2' in the zeroth index position in the queue1.   
ouput: '{7, 1, 9, 9, 7} 

* ****insert(index, queue_element):****

  It is used to insert the queue element in the particular index position.  
  Expression: insert(0, 2)- It insert the array element '2' in the zeroth index position in the queue1.  
 output: '{ 2, 7, 1, 9, 9, 7}  

The below Figure.1 shows the output for size(), delete(), insert() Methods of Queue.
  
![newqueue1](https://user-images.githubusercontent.com/110412474/186829636-ba817def-7c37-4c16-9f50-af55f1bc9f84.JPG)


                          Fig.1: Queue Method Example.1
 
Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method1/queue.sv

Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method1/queue_data_type.log

---

Example.2 : consider the variable size queue named as  
 queue1 ={"manipal", "bangalore", "udupi"};   

* ****pop.front():****
  
It remove the queue element from the front of the queue and return the first queue element.  
 In the above example, the array element from the front of the queue1 is removed i.e "manipal".        
 Now  After removing the array element the queue1 as the elements. queue1 ={ "bangalore", "udupi"};

* ****pop.back():****
  
It remove the queue element from the back of the queue and return the queue last queue element.  
  In the above example, the array element from the back of the queue1 is removed i.e "udupi".    
  Now After removing the array element the queue1 as the elements. queue1 = `{"bangalore"}
  
* ****push.front():****
  
It insert the queue element to the front of the queue.  
 Expression: push.front("yelahanka") - Insert the array element to the front of the queue1.  
  After push.front() the array elements of queue1 is '{"yelahanka", "bangalore"}  
  
* ****push.back():****
  
It insert the queue element to the back of the queue.  
  Expression: push.back("udupi")- Insert the array element to the back of the queue1  
  After push,back() the array elements of the queue1 is '{"yelahanka", "bangalore", "udupi"}

The below Figure.2 shows the output of pop.front(), pop.back(), push.front(), push.back(), Methods of Queue.
  
![newqueue2](https://user-images.githubusercontent.com/110412474/186828222-396f58a1-fdb4-4e89-88a6-506185f9495a.JPG)

                             Fig.2:Queue Method Example.2
 Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method2/queue.sv

 Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method2/queue_data.log
    
---

# Array Manipulation Method
In the System Verilog the array Manipulation method are the built in method used to searching and ordering. The array manipulation method iterate through the each array element to evaluate the expression given by the with clause. The with clause is must for the some of the method and for some it is optional. "with" is refer to evaluate the existing array with the conditions.The below figure shows the Flow chart of Array Manipulation Method

![Array Manipulation Method](https://user-images.githubusercontent.com/110412474/186419438-45f9dc16-d26b-4846-a7a1-ba8c3da67a46.jpg)
 
                                        Fig.1: Flow chart of Array Manipulation Method
## Array Manipulation Method Cheat Sheet
Method | Description
-- | --
find() | Returns all elements satisfying the given expression
find_index() | Returns the indices of all elements satisfying the given expression
find_first() | Returns the first element satisfying the given expression
find_first_index() | Returns the index of the first element satisfying the given expression
find_last() | Returns the last element satisfying the given expression
find_last_index() | Returns the index of the last element satisfying the given expression
max() | Return the element which as maximum value
min() | Return the element which as minimum value
unique() | Return the all elements which as unique value
unique_index() | Return the all index place which as unique value
reverse() | Reverse the order of array element
sort() | sort the array element in ascending order
rsort() | sort the array element in descending order
shuffle() | shuffle the array element such that the value of index is in Randomized order
sum() | return the sum of all the element
product() | return the product of all the element
and() | Return the bitwise AND(&) of all the element
or() | Return the bitwise OR of all the element in an array
xor() | Return the bitwise XOR(^) of all the element in an array

              Table.1: Array Manipulation Method
## Array locator Method
We declare the array with some elements by using the array locator method we can filter the values of the existing array by using the with clause evaluation conditions and all the element satisfyingly the condition are put in an array or return the value. The array locator method uses the with clause  for the below methods,

Example:  consider the array of five elements, shown the output in Fig.2.1:, 

array[5] = {"bangalore", "yelahanka", "maruthinagar", "oldtown", "newtown"};  

The ASCII value for b=098, y=121, m=109, o=111, n=110.  

Note: Here the comparison happens with the each ascii character of a string with the another string's of each ascii character sequentially. If the first ascii value of each character of a string is same, then it will compare the next ascii character of a string.  

* ****find():****  

This method is used to find the value in the existing array based on with clause conditional expressions.

Expression: result = array.find(check) with (check >="oldtown)"  
It will find the string from the existing array based on the condition (check >="oldtown), here the ascii value of 'y' is greater than o ,so it will print the output '{"yelahanka", "oldtown"}.


* ****find_index():****  

It is used to write the indices of all the element which satisfy the condition or given expressions.

Expression :  a = array.find_index(check) with (check =="yelahanka");  
It will find the index position of the string "yelahanka" and print the output index position of string "yelahanka" as '{1}.

* ****find_first():****

Write the first element which satisfy the given expression or condition and does not check the condition for other element in the array it will return only the first element.

Expression : result = array.find_first(check) with (check < "yelahanka" & check >= "newton" );
It will find the string which will satisfy the condition, here the 'o' has great ascii value than n and lesser than y, so it will return the first string from the output array as '{"oldtown"}.   

* ****find_first_index():****  

Used to return the first index of an array based on the given condition. 

Expression: a = array.find_first_index(check) with (check < "yelahanka");  
It will find the index position of the string if the string match with the condition then it will print the index position of matched string it will not check for the other string character in the existing string it only print the first index position of an array, here 'b' as less ascii value compared to 'y', so the output is '{0}. 

* ****find_last():****

Return the last value of the array which satisfy the given expression the given expression is evaluate for whole existing array, then the resultant array last element is used to display.

Expression :  result = array.find_last(check) with (check < "oldtown");  
It will find all the array element which will match the condition, here 'b', 'm' and 'n' are having less ascii value compared to 'o', so it will print only the last array element as '{"newtown"} .

* ****find_last_index():****  

Return the last index of the array which satisfy the given expression the given expression is evaluate for whole existing array, then the resultant array last element index is used to display.

Expression:  a = array.find_last_index(check) with (check < "oldtown");  
It will find all the index position of the element which will match the condition, here 'b', 'm' and 'n' are having less ascii value compared to 'o', so it will print only the last array index position as '{4} . 
 
The below Figure 2.1 shows the output of Array locator methods of function find()

![newarrayfind](https://user-images.githubusercontent.com/110412474/186823831-8aa6de65-6db3-446e-8c13-b9b541aca0aa.JPG)
                                      
                                               Fig.2.1: Array Locator Method 
Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_find/array.sv

Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_find/arrayfind.log


------
# The Array Locator Method optional 'with' clause

****Example****: consider array of five elements, shown the output in Fig:2.2

array[8] = {1,9,9,7,2,7,0,6}

*  ****min()****:

Write the element with minimum value or based on the condition that is evaluated to minimum.  
In the above example, the minimum value is 0, so output: '{0}.

* **max()**:

Write the element with maximum value or based on the condition that is evaluated to maximum.  
In the above example, the maximum value is 9, so output: '{9}

* ****unique()****:

 It will return the unique value form the array, if the values are repeated it will return only once.  
So the output for above example is, '{0,1,2,6,7,9}.

* ****unique_index()****:

Return the array element index whose values are different based on the unique expression/condition return the index of each different/unique values  
Expression: unique_index(): Return all the indices which is having the unique value. output = '{6,0,4,7,3,1}  

The below Figure 2.2 shows the output  for display the minimum value, maximum value , unique value and unique indices function of Array Manipulation Method.   

![newmax2](https://user-images.githubusercontent.com/110412474/186824043-319638ce-3631-427c-89c4-1a27dd814504.JPG)
                                      
                                            Fig.2.2:Array Locator Method
Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_max/arraymax.sv

Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_max/arraymax.log

-----------

# Array Ordering method

The Array ordering method used to sort the array in reverse manner, sort the element in ascending and descending order.

Example: consider the array of eight element, shown the output in Fig.3:

array[8] : {2,7,1,9,9,7,0,6}

* ****Reverse():****

Return the Array element in the reverse order.  
 Output for above example is, '{6,0,7,9,9,1,7,2}.

* ****sort():****

Sort the array element in the ascending order.  
So Output = '{0,1,2,6,7,7,9,9}

*  ****rsort():****

Sort the array elements in the descending order reverse of sort() method.  
So Ouptut = '{9,9,7,7,6,2,1,0)

* ****shuffle():****

Shuffle the order of the array element such that the index position of the existing array does not match with the resultant array. we can use the loop to shuffle the location of the array element.  
Expression: shuffle() - shuffle the array element such that the indcies place value should be different for each shuffle
for loop is used to shuffle the array elements
 output: 1st shuffle:'{9,0,9,2,7,6,7,1}  
         2nd shuffle:'{2,7,7,1,9,9,6,0}  
         3rd shuffle:'{1,0,6,9,7,7.2.9} 

The below Figure.3 shows the output of Array Ordering Method.

![neworder3](https://user-images.githubusercontent.com/110412474/186827961-0f1a61c5-c71e-4e70-90ce-2ddaf9c95a7c.JPG)


                                           Fig.3: Array ordering method

Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_ordering/arrayorder.sv

Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_ordering/array_order.log

------------

# Array Reduction Method  

Example: consider array of four element, shown the output in Fig.4: 
array[4]: {2,7,0,6}  

* ****sum():****

Return the output by adding the all the element in the existing array.
Here 2+7+0+6 = 15  
So, output : 15  

* ****product()****:

Return the output by multiplying the all the element in the existing array.  
Here 2*7*0*6 = 0
 So, output: 0

* ****and():****

Return the output by doing the bitwise AND (&) operation to the all array element.  

    Here   010    
           111    
           000    
     (&)   110    
    output:000

* ****or():****

Return the output by doing the bitwise OR(|) operation for all array element.  
    
     Here   010      
            111      
            000      
      (|)   110   
    ouptut: 111    

*  ****xor():****

Return the output by doing the bitwise XOR(^) operation for all array element  

       Here   010      
              111      
              000      
        (^)   110   
      ouptut: 011    

The below Figure.4 shows the output for Array Reduction Method.



![newreduction4](https://user-images.githubusercontent.com/110412474/186825000-4e4f6341-d933-47e1-8638-4fad88e1d0f5.JPG)
                                      
                                                     Fig.4:Array Reduction Method

Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_Reduction/arrayreduction.sv


Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_Reduction/array_reduction.log
