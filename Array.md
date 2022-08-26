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
