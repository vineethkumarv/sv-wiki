# Arrays
An array is a collection of elements, all of the same type, and accessed using its name and one or more indices. Verilog 2001 required that the low and high array limits must be part of the array declaration. System Verilog has introduced the compact array declaration style, where just giving the array size along with the array name declaration is enough.

The below figure shows the different types of arrays used in System Verilog.
![arrays_sv](https://user-images.githubusercontent.com/110448056/186146778-a5174960-8e33-42df-845e-d1fd2bc1b1f3.png)

                                                     Fig.1 Types of arrays in SV

## Arrays cheat sheet

**Sr No.** | **Arrays Types**         | **Description**                                                                   | 
|---|------------------------------------------ | -------------------------------------------------------------------------------------|
1|[Packed Array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Array#packed-arrays) | Dimension of array declared before array name declaration |       
2|[Unpacked Array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Array#unpacked-arrays) | Dimension of the array declared after array name declaration | 
3|[Dynamic Array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Array#dynamic-arrays) | Memories will be allocated at run time |
4|[Associative Array](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Array#associative-arrays) | Memories allocated only when it is used and any index type is used for indexing the array |
5|[Queue](https://github.com/muneeb-mbytes/SystemVerilog_Course/wiki/Array#queue) | It is similar to fifo and we can add and remove elements from queue at run time |

                                       Table.1. Array cheat sheet

## Static Arrays(Fixed size arrays):
In fixed size array / Static arrays, array size will be constant throughout the simulation, Once the array is declared no need to create it. By default, the array will be initialized with value ‘0’. In this type of arrays memories will be occupied during compilation stage and we can't able to rellocate the memories at run time.

Static arrays has two types: 1) Packed Arrays 2) Unpacked Arrays.

---

### Packed Arrays:
A packed array is one where the dimensions of the array is declared before the array name. In this multiple bits of array stored in one memory location.

**Note:-** It can be made of any single bit data types bit, logic and reg. we can't use multi bits data types for packed arrays.
 
**Syntax:-** `[data_type] [dimensions] [array_name];`

**Example,** 

`bit [3:0]abc = 4'b0110`  
`logic [15:0]pqr = 16'h10fe`  
`reg [7:0]xyz = 8'd16`

**Some Points about packed arrays:**

*  If a packed array is declared as signed, then the array viewed as a single vector shall be signed. The individual elements of the array are unsigned unless they are of a named type declared as signed.
* The maximum size of a packed array can be limited, but shall be at least 65536 (2^16) bits.
* Packed arrays are synthesizable.

The below figure shows the output of single dimension packed array, here packed array consists of reg, logic and bit data type as mentioned in the above example.

![single_packed](https://user-images.githubusercontent.com/110448056/186883341-d960ed62-8e66-4ff9-b729-2f03c7ffd57f.png)

                                   Figure.2 single dimension packed array ouptut

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/packed_array/single_packed/packed_array.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/packed_array/single_packed/packed_array.log
 
The below figure shows the output of multi dimension packed array, here it consists of bit [2:0][3:0]xyz = 12'hdfe.
Here, 2 dimensional packed array declared and and we can similarly create 3 dimensional array as same.

![multi_packed](https://user-images.githubusercontent.com/110448056/186884901-0dfbfccd-c15f-4677-b9d3-8c394994a6b8.png)

                                  Figure.3 multi dimensional packed array output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/packed_array/multi_packed/multi_packed.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/packed_array/multi_packed/multi_packed.log

**Applications of packed arrays:**

They are used to store packet structures on which bit-select and part-select operations could be performed.

---

### Unpacked Arrays:
A unpacked array is one where the dimensions of the array is declared after the array name. In this multiple bits will be stored in different memory locations.

**Syntax:-**  `[data_type] [array_name] [dimension];`

**Example,** 

`byte a[8] = '{4,5,6,2,3,7,9,10}`

`int abc[10] = $urandom_range(10,50);` 

where, $urandom_range is inbuilt function which generates random numbers between 10 to 50.

**Some Points about unpacked arrays:**

* They can be of any data type.
* If an unpacked array is declared as signed, then this applies to the individual elements of the array, since the whole array cannot be viewed as a single vector.
* The unpacked dimensions can be arranged in memory in any way that the simulator chooses – does not have to be contiguous.
* They could be fixed-size arrays, dynamic arrays, associative arrays or queues.
* Unpacked arrays are Non-synthesizable.

The below figure shows the output of single dimension unpacked array.

![single_unpacked](https://user-images.githubusercontent.com/110448056/186889154-0f23c201-ca8b-47cd-ae46-8fcd3c0d0cfd.png)

                                  Figure.4 single dimensional unpacked array output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/unpacked_array/single_unpacked/unpacked.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/unpacked_array/single_unpacked/unpacked_array.log

The below figure shows the output of multi dimension unpacked array, here it consists of `int abc[2][3] = $urandom_range(10,50)`.
Here, 2 dimensional packed array declared and and we can similarly create 3 dimensional array as same.

![multi_unpacked](https://user-images.githubusercontent.com/110448056/186889779-c6758475-6199-4e4e-9cbf-e25e0e2abd29.png)

                                 Figure.5 multi dimensional unpacked array output
          
**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/unpacked_array/multi_unpacked/multi_unpacked.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/unpacked_array/multi_unpacked/multi_unpacked.log

**Applications of unpacked arrays:**

They are used to model Random Access Memories (RAMs), Read Only Memories (ROMs) and register files where one element is accessed at a time.

---

## Mixed Multi Dimensional Arrays:
Mix of Packed arrays and unpacked arrays are known as mixed multi dimensional array. 

**Syntax:-**  `[data_type] [dimensions] [array_name] [dimensions];`

**Example,** 

`logic [2:0][3:0] mixed_array [2:0][3:0];`

**Some Points about mixed multidimensional arrays:**

* All unpacked dimensions are first referenced from the left-most to the right-most dimension in that order. 
* All packed dimensions are then referenced from the left-most to the right-most dimension in that order.

In the given example, going from left to right side the memory will be allocated and for that first unpacked array dimension are considered as shown in diagram below and after that packed array dimensions are considered.

![mixed-arrays](https://user-images.githubusercontent.com/110448056/187194239-d189bcf7-1b64-407a-b35b-ec1e8fdce5cf.png)

                               Figure.6 mixed multi dimensional array memory allocation

--- 

## Dynamic Arrays:
A dynamic array is an unpacked array whose size can be set or changed at run time. The space for a dynamic array does not exist until the array is explicitly created at run-time. 

**Syntax:-** `<data_type> array_name []`

**Example,**

`int abc[] = new[7];`

`abc[7] = '{11,12,13,14,15,16,17};`

**Some Points about unpacked arrays:**

* The default size of an un-initialized dynamic array is 0.
* Dynamic arrays support all variable data types as element types, including arrays.
* An out-of-bound access in a dynamic array leads to a default value of the data type.

**Dynamic Arrays Methods cheat sheet:**

Sr No. | **Methods**         | **description**                                                                   | 
|---|------------------------------------------ | -------------------------------------------------------------------------------------|
1|constructor new [value] | Sets the size of a dynamic array and initializes its elements or changes the size of the array at run-time. If the value is zero, the array shall become empty. If the value is negative, then it is an error.   |       
2|function int size() | The size() method returns the current size of a dynamic array or returns zero if the array has not been created| 
3|function void delete() | The delete() method empties the array, resulting in a zero-sized array|

                                 Table.2. dynamic array methods

The below figure shows the output of dynamic array.

![dynamic](https://user-images.githubusercontent.com/110448056/186890744-7a0a6733-b3a1-4e87-ae49-7956d8b5a7d1.png)

                                 Figure.6 dynamic array output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic/dynamic.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic/dynamic_array.log

The below figure shows the output of dynamic array methods.
In example,

`int xyz[] = new[10];`

`xyz = '{11,12,13,14,15,16,17,18,19,20};`

![methods_dynamic](https://user-images.githubusercontent.com/110448056/186891136-81fbb195-14c4-42b0-b355-fb280346ecc7.png)

                              Figure.7 dynamic array methods output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic_method/methods.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic_method/methods_dynamic.log    

The below figure shows the output of out-of-bound access in a dynamic array leads to default value of data_type.
In example,

`int da[] =new[5];`

`da[5] = '{1,2,5,6,8};`

`out of bound access of dynamic array da[1024] = 0;`

![dynamic](https://user-images.githubusercontent.com/110412474/187175379-fa7e35e3-df71-4421-a5dd-a5fcabb4fb84.JPG)

                                 Fig:7.1 out-of-bound access of Dynamic array  

**Github lab code link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic_unbound/dynamic.sv

**Github lab output link:** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/dynamic_array/dynamic_unbound/dynamic.log

**Applications of dynamic arrays:**

A dynamic array that can be allocated and re-sized during simulation will avoid this unnecessary memory allocation.

---

## Associative Arrays:

An associative array is an unpacked array data-type. It does not have any storage allocated until it is used, and the index type used to access elements is not restricted to integers.

**Syntax:-** `<data_type> array_name [index_type]`

where, index type is any data type or it's wildcard "*".

**Example,**

`int abc[*];`

`abc  = '{ 1:20, 25:22, 38:66};`

`string pqr[string];`

`pqr = '{"fruits":"mango" , "vegetables":"cucumber" , "season":"monsoon"};`

**Some Points about unpacked arrays:**

* Associative array elements are unpacked.
* It can be stored by the simulator as a hash (lookup) table for extremely fast access of its elements. A hash table contains an array of groups of elements. A function called hash function generates a unique key to compute the index into this array, from which the correct array element value is obtained.
* Elements in an associative array can be accessed in a similar way as those in a one-dimensional array.
* If an attempt is made to read an invalid (non-existent) associative array entry, then the simulator will issue a warning and will return the value ‘x’ for a 4-state integral type or a value ‘0’ for a 2-state integral type.

**Associative Arrays Methods cheat sheet:**

Sr. No| Function | Description
|-- | -- | --
1|function int num () | Returns the number of entries in the associative array
2|function int size () | Also returns the number of entries, if empty 0 is returned
3|function void delete ([input index]) | index when specified deletes the entry at that index, else the whole array is deleted
4|function int exists (input index) | Checks whether an element exists at specified index; returns 1 if it does, else 0
5|function int first (ref index) | Assigns to the given index variable the value of the first index; returns 0 for empty array
6|function int last (ref index) | Assigns to given index variable the value of the last index; returns 0 for empty array
7|function int next (ref index) | Finds the smallest index whose value is greater than the given index
8|function int prev (ref index) | Finds the largest index whose value is smaller than the given index

                                  Table.3. associative arrays methods

The below figure shows the output of associative array.

![associative](https://user-images.githubusercontent.com/110448056/186892320-543d76d4-30e2-4f1b-adbc-dd9a68969c25.png)

                               Figure.8. associative array output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/associative_array/associative/associative_array.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/associative_array/associative/associative_array.log

The below figure shows the output of associative array methods.
In example,

`int abc[string];`

`abc = '{"vadodara" : 10, "ahmedabad" : 25, "rajkot" : 55, "surendranagar" : 38 };`

![associative_methods](https://user-images.githubusercontent.com/110448056/186893146-f5b8990d-8c3b-44b6-8301-cecbb722c2bb.png)

                                Figure.9. associative methods output

**Github lab code link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/associative_array/associative_methods/associative_methods.sv

**Github lab output link:-** https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/associative_array/associative_methods/associative_mthod.log


**Applications of associative arrays:**

Associative arrays used to design Content Addressable Memories (CAMs). Random read or write tests for verification of memories could use associative arrays for storing data only for addresses which have been written. This would take up significantly much lesser memory than the entire array normally used in Verilog.

---

# Queue
Queue is a datatype used to have the variable size ordered collection of same datatypes in unpacked array format, it is used to insert the element in the array and delete the element in the array by both the ends. It is like buffer, used to model the first in first out(FIFO) and last in first out (LIFO).

****Syntax****: `data_type name[$];`
                 
data_type - data_type of queue element  
name - name of the queue  
[$] - declare the unbounded queue  

There are two types of queue declaration

## 1. bounded

 The queue as the size limit. we need to provide the max value while declare the queue 
 
syntax: `data_type name[$:255];`
 
Here $- first element
255 - last element

![bounded queue](https://user-images.githubusercontent.com/110412474/186423427-f222976c-7179-40ac-83fb-0ae011222e72.jpg)

                            Figure.10. Bounded queue with push and pop operation



---


## 2. unbounded

 The queue as no size limit. we do not provide an size of queue it is a variable size queue.
 
syntax: `data_type name[1:$];`
     
Here 1 - first element
$ - last element


![unbounded queue](https://user-images.githubusercontent.com/110412474/186423948-b22286aa-8de7-4dde-9b0e-08bbdf394306.jpg)

                            Figure.11. Unbounded queue with push and pop operation                         

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
  
                    Table.4 Queue Methods
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


                          Figure.12. Queue Method Example.1
 
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

                             Figure.13. Queue Method Example.2

 Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method2/queue.sv

 Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Queue/queue_method2/queue_data.log
    
---

# Array Manipulation Method
In the System Verilog the array Manipulation method are the built in method used to searching and ordering. The array manipulation method iterate through the each array element to evaluate the expression given by the with clause. The with clause is must for the some of the method and for some it is optional. "with" is refer to evaluate the existing array with the conditions.The below figure shows the Flow chart of Array Manipulation Method

![Array Manipulation Method](https://user-images.githubusercontent.com/110412474/186419438-45f9dc16-d26b-4846-a7a1-ba8c3da67a46.jpg)
 
                                        Figure.14. Flow chart of Array Manipulation Method
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

              Table.6. Array Manipulation Method
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
 
The below Figure 15 shows the output of Array locator methods of function find()

![newarrayfind](https://user-images.githubusercontent.com/110412474/186823831-8aa6de65-6db3-446e-8c13-b9b541aca0aa.JPG)
                                      
                                               Figure.15. Array Locator Method 
Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_find/array.sv

Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_find/arrayfind.log


------
# The Array Locator Method optional 'with' clause

****Example****: consider array of five elements, shown the output in Figure.16

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
                                      
                                            Figure.16. Array Locator Method
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


                                           Figure.17. Array ordering method

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

The below Figure.18 shows the output for Array Reduction Method.



![newreduction4](https://user-images.githubusercontent.com/110412474/186825000-4e4f6341-d933-47e1-8638-4fad88e1d0f5.JPG)
                                      
                                                     Figure.18. Array Reduction Method

Github lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_Reduction/arrayreduction.sv


Github lab output link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/sv_arrays/Array_methods/Array_Reduction/array_reduction.log
