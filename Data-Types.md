# Data Types

In Verilog, all the data types were of 4-state, i.e., it could represent 0, 1, X and Z. However, in the case of test benches, these 4-state variables were not required. For example, to count the number of packets, we would require a 2-state variable. Thus, System Verilog introduces a new class of variables of 2-states, i.e., 0 and 1. 

![new_data_types](https://user-images.githubusercontent.com/110448382/186157987-25bc0cd1-655e-4576-b156-3b40b7350253.png)

---


## 2 and 4 state data type cheat sheet  

sr. no. | **data type**         | **2-state/4-state** |   **bit**  |  **signed/unsigned**  |
|:--|:---------------------- | :-------------|:-----------------|:-----------------------|
|1.|logic |   4 | >=1 | unsigned  | 
|2.|integer | 4 | 32  | signed   |
|3.|time | 4 | 64 | unsigned  |
|4.| real | 4 | 64 | unsigned |
|5.|bit |   2 | >=1 | unsigned  | 
|6.|byte | 2 | 8  | signed   |
|7.|shortint | 2 | 16 | signed  |
|8.| int | 2 | 32 | signed |
|9.| longint | 2 | 64 | signed |

---

****Signed and Unsigned numbers****

****Unsigned number****:The unsigned numbers do not use any flag for the sign, i.e., only positive numbers can be stored by the unsigned numbers.  
The range of the unsigned binary numbers starts from 0 to (2^n-1), n represents number of bits.

****Signed numbers****:The positive and negative values are differentiated by using the sign flag in signed numbers. Signed bit makes two possible representations of zero (positive (0) and negative (1)).  
The range of the signed binary numbers starts from  -2^(n-1)+1 to 2^(n-1)-1, n represents number of bits.  
There are the following types of representation of signed binary numbers:

1. ****Sign-Magnitude form****
In this form, a binary number has a bit for a sign symbol. If this bit is set to 1, the number will be negative else the number will be positive if it is set to 0. Apart from this sign-bit, the n-1 bits represent the magnitude of the number.

2. ****1's Complement****
By inverting each bit of a number, we can obtain the 1's complement of a number. The negative numbers can be represented in the form of 1's complement. In this form, the binary number also has an extra bit for sign representation as a sign-magnitude form.

3. ****2's Complement****
By inverting each bit of a number and adding plus 1 to its least significant bit, we can obtain the 2's complement of a number. The negative numbers can also be represented in the form of 2's complement. In this form, the binary number also has an extra bit for sign representation as a sign-magnitude form.

---

## Four state data type

The below tabular column represent the 4 different state.  

 | **State**         | **Description**                                                                   | 
|:------------------------------------------ | :-------------------------------------------------------------------------------------|
|0 |    Logic state 0 |       
|1|Logic state 1 | 
|x or X | Logic state unknown|
| z or Z|Logic state high impedance |


---

### 1) Logic

The logic data type is a 4 state type that can take values 0,1,x and z. logic data type which can be used in place of both the wire and reg data types because wire data type does not have multiple drivers.  
By default logic data type is unsigned and its initial value is x. logic data type can be driven in both procedural block and continuous assign statements.

### syntax:
`logic variable_name;`


---

## 2. integer

integer is 4-state data type, integer can be either 0,1,x and z which represent a 32-bit signed number. Default value of integer is x. integer can hold values ranging from -2^31 to (2^31)-1.

****Syntax :**** `integer variable_name;`  
****Example :**** `integer data;`

The below figure shows the output of integer data type.

![integer](https://user-images.githubusercontent.com/110448382/186824975-f4a0493d-fe8d-4da9-8c6d-f9eaf43de032.png)

                                       Figure.2. integer output 

---

## 3. time

time is special data type for simulation time measuring. It is 4-state data type,represent 64-bit unsigned integer, that can be used in conjunction with the $time system task to hold current simulation time.

****Syntax :**** `time variable_name;`  
****Example :**** `time t;`       
`t=$time;`    

The below figure shows the output of time data type.

![time](https://user-images.githubusercontent.com/110448382/186825013-5d37ca86-66d8-4012-a437-d9b3c7f4d611.png)

                                     Figure.3. time output

---

## 4. real

The real data type implemented as a 64-bit real number. Real numbers can be specified in either decimal notation (4.43) or in scientific notation (42e8). Default value of real data type is 0.

****Syntax :**** `real variable_name;`  
****Example :**** `real data;`      
`data = 4.43;`   

The below figure shows the output of real data type.

![real](https://user-images.githubusercontent.com/110448382/186825049-8e139a76-5e2d-43f1-af75-f8e886d79ef3.png)

                                        Figure.4. real output

---

## 5. bit

bit is 2-state 32-bit unsigned integer which is used most often test benches. It can be either 0 or 1 which represents a single bit. Default value of bit data type is 0.

****Syntax :**** `bit variable_name;`  
****Example :**** `bit data;`        
`bit [0:31] data`    

The below figure shows the output of bit data type.

![bit](https://user-images.githubusercontent.com/110448382/186825098-59e5284a-6a0f-4fdc-8ad6-ff434a685832.png)

                                         Figure.5. bit output

---

## 6. byte

byte is 2-state data type which is used most often test benches. It can be either 0 or 1 which represent a 8-bit signed integer. Default value of byte is 0.

****Syntax :**** `byte variable_name;`  
****Example :**** `byte data;`   

The below figure shows the output of byte data type.

![byte](https://user-images.githubusercontent.com/110448382/186825136-81275ffc-0942-43fe-b7bf-5aa42ba24ca9.png)

                                  Figure.6. byte output

---

## 7. shortint 

shortint is 2-state data type. It can be either 0 or 1 which represent a 16-bit signed integer. Default value of shortint is 0.

****Syntax :**** `shortint variable_name;`  
****Example :**** `shortint data;`

The below figure shows the output of shortint data type.

![shortint](https://user-images.githubusercontent.com/110448382/186825172-17bb35a1-c1a4-4071-ad9f-6e45e9011b8f.png)

                                       Figure.7. shortint output

---

## 8. int 

int is 2-state data type which is used most often testbenches. It can be either 0 or 1 which represent a 32-bit signed integer. Default value of int is 0.

****Syntax :**** `int variable_name;`  
****Example :**** `int data;`

The below figure shows the output of int data type.

![int](https://user-images.githubusercontent.com/110448382/186825210-010b32ee-95c4-4c6e-b638-9f81ec703812.png)

                                      Figure.8.int output

---

## 9. longint 

longint is 2-state data type. It can be either 0 or 1 which represent a 64-bit signed integer. Default value of longint is 0.

****Syntax :**** `longint variable_name;`  

****Example :**** `longint data;`

The below figure shows the output of longint data type.

![longint](https://user-images.githubusercontent.com/110448382/186825249-c7470eb9-2738-4218-8d16-ce9634cd5c31.png)

                                        Figure.9. longint output

---

# enum

Enumerated data types defines a set of named values.

****Syntax**** : `enum enum_base_type(optional) { <enum_name_declaration> = constant_expr(optional)...} <enum_type_identifier>;`

* An enumerated type is stored as type ‘int’ unless specified as something else.
* This type automatically gives a unique value to every name in the list.
* Values default to the ‘int’ type starting at 0 and then incrementing by 1.
* If a value is not specified for a name, it gets the value of the previous name in the list incremented by 1.

---

sl.no|Method | Description
-- |-- | --
1|first() | returns the value of the first member of the enumeration
2|last() | returns the value of the last member of the enumeration
3|next() | returns the value of next member of the enumeration
4|prev() | returns the value of previous member of the enumeration
5|num() | returns the number of elements in the given enumeration
6|name() | returns the string representation of the given enumeration value


---

# String

A string type is a variable-length ordered collection of characters. The length of a string is the number of characters in the collection.

****Syntax**** :`string variable_name [= initial_value];`

****Example****: `string str = Manipal`

* The memory space for strings is dynamically allocated.
* The indices of string variables shall be numbered from 0 to N–1 (where N is the length of the string) so that index 0 is the first (leftmost) character of the string and index N–1 is the last (rightmost) character of the string.
* An un-initialized or empty string is represented with the special value “”. An empty string has 0 length. 

---

****String operators cheat sheet**** 

 Operation   | **Operator**         | **Description**                                                                   | 
|:---|:------------------------------------------ | :-------------------------------------------------------------------------------------|
Equality|str1==str2 | Returns 1 if the two strings are equal and 0 if they are not  |       
Inequality|str1!=str2     |Returns 1 if the two strings are not equal and 0 if they are| 
Comparison|Str1 < Str2, Str1 <= Str2, Str1 > Str2, Str1 >= Str2 |Returns 1 if the corresponding condition is true and 0 if false|
Concatenation|{Str1, Str2, ..., StrN}  | All strings will be concatenated into one resultant string                                        
Replication | {multiplier{Str}} | Replicates the string N number of times, where N is specified by the multiplier|
Indexing | Str[index] | Returns a byte, the ASCII code at the given index. If given index is out of range, it returns 0|

                                          Tabular column.1.string operators

****Example:****

Consider 2 strings, str1 as Manipal and str2 as Udupi,
  
* ****Equality operator**** (str1 == str2), here the string 1 each letter ASCII value will be compared with string 2's of each letter sequentially, if it is equal then it will return 1 or else 0, here instead of 1 and 0 we're using statements. In this example, strings are not equal, because the ascii value of U is 85 and M is 77. Here the first letters ascii value are not same so it will display as strings are not equal.

* ****Inequality operator**** (str1 != str2) , here the string 1 each letter ASCII value will be compared with string 2's of each letter sequentially, if it is not equal then it will return 1 or else 0, here instead of 1 and 0 we're using statements. In this example, strings are not equal, because the ascii value of U is 85 and M is 77. Here the first letters ascii value are not same so it will display as strings are not equal.

* ****Comparison operator****(>, => ,<, =<), here the string 1 each letter ASCII value will be compared with string 2's of each letter sequentially, here it will check for >, => ,<, =< condition, if any of these becomes true, it will return 1. Here as we discussed in the above points, U as large ascii value, so here string1 < string2 and string1 =< string2.

* ****Concatenation operator**** ({str1,str2}), here 2 strings are concatenated and resultant is single string. So output will be ManipalUdupi.

* ****Replication operator**** ({2{str1}}), here it replicates the string N number of times, where N is specified by the multiplier. Here we're considering N as 2, so string1 will be replicated 2 times, and the output is ManipalManipal.

* ****Displaying index letter**** (str1[i]), here we'll get the ascii character at mentioned index number. In this case, we've included for loop to display all the ascii characters of a string, so we get the output as   
M  
a  
n  
i  
p  
a  
l  


The below figure.1 illustrates the output for string operators

![string_oper2](https://user-images.githubusercontent.com/110443214/186822122-a5f85160-9938-41d3-811f-5b155df68cb2.png)


                                   Figure.1. Output of string operators


---


****String Methods cheat sheet**** 

Function | Description
-- | --
str.len() | Returns length of string.
str.putc() | Used to assign one character of string.
str.getc() | Returns a character.
str.tolower() | Returns the lowercase of string.
str.toupper() | Returns the uppercase of string.
str.compare(s) | Returns the string compare result as ascii value.
str.icompare(s) | Returns caseless string compare result as ascii value.
str.substr(i,j) | Returns the sub string of main string.

                 Tabular column.2. string methods

****Example:****

Consider a string Manipal,

* ****str.len()****, here it will give the length of a string. As we considered Manipal, here there are 7 ascii character. So the output is 7.

* ****str.putc()****, it is used to assign one character of a string. So consider one temp variable to store the changes of the string and assign character "t" for 3rd index as given temp.putc(3, "t"). And the output we'll get as Mantpal.

* ****str.getc()****, it returns a character as output. Here mention the index of a character, which we want to get as output as given str.getc(1). And the output we get as a.

* ****str.tolower()****, it gives a string in lowercase. So the output will be manipal.

* ****str.toupper()****, it gives a string in uppercase. So the output will be MANIPAL.

* ****str.compare(s)****, it will compare the string and gives output in ascii value. To make comparison, declare one more string as mirafra, and compare Manipal with mirafra. Here comparison will takes place with each character of a string Manipal with the each character of mirafra sequentially. Here ascii value of M = 77 and m = 109. So the difference between 77-109 is -32. So we get the output as -32.

* ****str.icompare(s)****, it will compare the string without considering the cases of letters, and gives output in ascii value. As mentioned above, the strings are Manipal and mirafra, here it's a case insensitive comparison, M and m will consider as same, and next letters are a = 97 and i = 105, hence the difference between them is (97 - 105) -8. So the output is -8.

* ****str.substr(i,j)****, it gives the sub string of main string. So we should mention the sub string indices which are to be displayed as given, str.substr(1,2). In Manipal the 1 and 2 index ascii characters are a and n. So the output will be an.


The below figure.2. shows the output of string methods.

![string_method2](https://user-images.githubusercontent.com/110443214/186822759-93e298e7-88c9-4c73-b300-54e0bf76a383.png)

                                          Figure.2. Output of string methods


















# **Structure**  

 A structure contains different data types with different sizes which grouped under one single structure name. Structure  is originally unpacked form by default, but we can use 'packed' keyword  for converting  into packed structure. Structure is different from normal array because array uses only same type of elements with sizes whereas structure uses different data types. The unpacked structure declared using 'struct' keyword.    
 
The below figure shows different types of structures in System Verilog.
![image](https://user-images.githubusercontent.com/110484152/186200139-5258a878-c717-4c94-8fa4-33a53a8d7680.png)  

                                                Fig 1: Structure Diagram  

## **Unpacked Structure**  
 
Unpacked structure is the default structure syntax and is same as normal structure. The different variables holds different data inside the structure known as members of the structure. Structure members were treated as independent variables. when we want to assign values to  the members of structure, then use 'structure name. variable'.    

#### Assignments To Struct Members:

structure name = '{value1, value2, value3};   

#### Alternate Method to assign values:  
 
 structure name = '{variable1 : value1 , variable2 : value2 , variable 3 : value3};  
This method gives initialization done in one step. The variable and value can be separated by a colon '.' .


### **Syntax:**

`struct{`    
        `list of  different types of variables with sizes`      
      `} structure name;`    

### **Example:**    
 
`struct{` 
       `string name;`   
       `int salary;`  
       `byte id;`  
       `} employee;`    



### **Output:**   
   
The below output shows the unpacked structure.
![s1](https://user-images.githubusercontent.com/110484152/186596674-18bb7ee5-7000-4f59-aa2b-8909b0c94c66.png)

                                                      Fig 2: Unpacked structure  

The above output illustrates that the unpacked structure contains the different datatypes like string, int, byte etc. The string must be initialised within double quotes only. The variables like int , byte can be assign the value itself



## **Packed structure**  
 
Packed structure can explicitly done using packed keyword. It stores all members of structures in the form of contiguous form in a specified order.
In RTL code, a packed structure is treated as a single vector and each data type in the structure is represented as a bit field. The whole structure is packed together in memory without gaps. Only packed data types like bit , logic  and integer data types are also  allowed to use  in a packed structure.

Note: Structure cannot be packed if it cannot be represented as a vector.     

### **Syntax:**  

`typedef struct packed{`  
`list of  different types of variables with sizes`  
`} structure name;`   

### **Example:**     

`typedef struct packed{`  
`byte id;`  
`bit[7:0]experience;`   
`logic[15:0]salary;`  
`}employee_ details;` 

### **Output:**     

The below output shows that output of packed structure  
![ps1](https://user-images.githubusercontent.com/110484152/186596534-8471a1dd-bdf0-401f-bfc7-2ecedd59157a.png)  

                                            Fig 3: Packed structure  

The above output illustrates the output of packed structure. It contains the different datatypes like bit , logic . We can assign values and  display as output. Here we cannot  use string dataype inside the packed structure because string cannot be treated as single vector. It will show compile error.   


----


# **Typedef**    

Typedef used to create new identifiers from longer datatype specification. It  is similar to alias command. Typedef uses mainly in complex testbenches in System Verilog because it replaces the longer datatypes like int(unsigned longint, signed shortint), byte ,bit[7:0],logic[7:0] with identifiers in the code. Typedef uses in Class, Structure and  Enumeration to  make the datatype declarations  easier.  
  
### **Syntax:**  

`typedef <base_type> <size> <type_name>;`  

## **Typedef in Class**   

The main use of Typedef in class is that sometimes we use class variable before the declaration of the class itself. At that time it will cause some compile errors to the code. So avoid that compile errors , we can use 'typedef class variable' before the declaration of class itself.   
  
### **Syntax:**  

`typedef class class_name;`

### **Example:**    

`typedef class fruit2;`   
`class fruit1;`    
`fruit2 f;`  
`endclass` 

`class fruit2`    
`fruit1 f;`  
`endclass`  

### **Output:**    

The below figure shows that output of typedef with class.
![typedef class](https://user-images.githubusercontent.com/110484152/186602737-1d67bede-f186-4483-822b-cc8d808c1f21.png)  

                                                   Fig 1 : Typedef with class  

The above example and output shows that how typedef avoids the compiler error in class1 because class2 declaration is not done  at that time. If we didn't use 'typdef class2' at the beginning , it will show some compiler error. It will display the text given inside the $display.

## **Typedef in Structure**  

Without Typedef, Structure may happen some compile errors in large complex testbenches. Typedef also provide declarations make more easier.  

### **Syntax:**     

`typedef struct {`   
         `datatype name;`  
         `datatype name;`  
         `}structure_name;`  

### **Example:**   
 
`typedef struct{`  
`string name;`  
`byte id;`   
`longint age;`   
`} personal_ details;` 

### **Output:**    

The below figure shows the output of typedef with structure datatype.
![12](https://user-images.githubusercontent.com/110484152/186636386-2301edc3-eda9-498c-b038-84e4c3de68a4.png)  

                                                    Fig 2: Typedef with structure  

The above output shows that typedef in structure decreases the usage of longer datatypes by creating new variable. We can see that in example 'longint' datatype changed to 'age' ,it is a new variable that is created by using typedef in structure.   
## **Typedef in Enumeration**   

Typedef uses for when we need more than one variable to share the same enumeration values. Without Typedef we will get syntax error. Enumeration datatype create new variable for all values.
 
### **Syntax:**    

 `typedef enum { values } <type_ name>;`

### **Example:**    

`typedef enum {RORITO,FLAIRFX,REYNOLDS} <e_ pen>;`

### **Output:**    

The below figure shows the typedef with 'enumeration datatype  
![typeenum](https://user-images.githubusercontent.com/110484152/186602985-64dd1698-8a5d-4951-9a30-523acc0ad1bc.png)  

                                             Fig 3 : Typedef with Enumeration 

The above output shows that enum datatype with typedef .If we didn't use typedef with enumeration datatype, it will show syntax error. The output shows that enumeration datatype created a new variable 'e_ pen' and initialize a variable 'pen'. After this, choose one value and assign to 'pen'. It will display the assigned value.   

