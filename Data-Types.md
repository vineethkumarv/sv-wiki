# Data Types

In Verilog, all the data types were of 4-state, i.e., it could represent 0, 1, X and Z. However, in the case of test benches, these 4-state variables were not required. For example, to count the number of packets, we would require a 2-state variable. Thus, System Verilog introduces a new class of variables of 2-states, i.e., 0 and 1. 

![new_data_types](https://user-images.githubusercontent.com/110448382/186157987-25bc0cd1-655e-4576-b156-3b40b7350253.png)



## data type cheat sheet  

sr. no. | **data type**         |
|:--|:---------------------- |
|1.|2-stage and 4-stage |
|2.|Arrays | 
|3.|Strings |
|4.|Structures |
|5.|Enumerated | 
|6.|User defined |

                                          Tabular column. indexing data type

---


## 2-state and 4-state data type cheat sheet  

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

                                          Tabular column.1. 2-state and 4-state data type

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

                                          Tabular column.2. value of 4-state
---

## 1. Logic

The logic data type is a 4 state type that can take values 0,1,x and z. logic data type which can be used in place of both the wire and reg data types because wire data type does not have multiple drivers.  
By default logic data type is unsigned and its initial value is x. logic data type can be driven in both procedural block and continuous assign statements.

****syntax :**** `logic variable_name;`  

****Example :**** `logic [2:0] logic_data_type;`


The below figure shows the output of logic data type.

![logic](https://user-images.githubusercontent.com/110448382/186890682-bfba09db-21ce-43ef-b991-379a5207ce5d.png)

                                       Figure.1. logic output 

Github lab link: 

Github lab output link: 

---

## 2. integer

integer is 4-state data type, integer can be either 0,1,x and z which represent a 32-bit signed number. Default value of integer is x. integer can hold values ranging from -2^31 to (2^31)-1.

****Syntax :**** `integer variable_name;`  

****Example :**** `integer integer_data;`

The below figure shows the output of integer data type.

![integer](https://user-images.githubusercontent.com/110448382/186824975-f4a0493d-fe8d-4da9-8c6d-f9eaf43de032.png)

                                       Figure.2. integer output 

---

## 3. time

time is special data type for simulation time measuring. It is 4-state data type,represent 64-bit unsigned integer, that can be used in conjunction with the $time system task to hold current simulation time.

****Syntax :**** `time variable_name;`  

****Example :**** `time time_data;`       
`time_data = $time;`    

The below figure shows the output of time data type.

![time](https://user-images.githubusercontent.com/110448382/186825013-5d37ca86-66d8-4012-a437-d9b3c7f4d611.png)

                                     Figure.3. time output

---

## 4. real

The real data type implemented as a 64-bit real number. Real numbers can be specified in either decimal notation (4.43) or in scientific notation (42e8). Default value of real data type is 0.

****Syntax :**** `real variable_name;`  

****Example :**** `real real_data;`      
`real_data = 4.43;`   

The below figure shows the output of real data type.

![real](https://user-images.githubusercontent.com/110448382/186825049-8e139a76-5e2d-43f1-af75-f8e886d79ef3.png)

                                        Figure.4. real output

---

## 5. bit

bit is 2-state 32-bit unsigned integer which is used most often test benches. It can be either 0 or 1 which represents a single bit. Default value of bit data type is 0.

****Syntax :**** `bit variable_name;`  

****Example :**** `bit single_data;`        
`bit [3:0] multi_bit_data;`    

The below figure shows the output of bit data type.

![bit](https://user-images.githubusercontent.com/110448382/186825098-59e5284a-6a0f-4fdc-8ad6-ff434a685832.png)

                                         Figure.5. bit output

---

## 6. byte

byte is 2-state data type which is used most often test benches. It can be either 0 or 1 which represent a 8-bit signed integer. Default value of byte is 0.

****Syntax :**** `byte variable_name;`  

****Example :**** `byte byte_data;`   

The below figure shows the output of byte data type.

![byte](https://user-images.githubusercontent.com/110448382/186825136-81275ffc-0942-43fe-b7bf-5aa42ba24ca9.png)

                                  Figure.6. byte output

---

## 7. shortint 

shortint is 2-state data type. It can be either 0 or 1 which represent a 16-bit signed integer. Default value of shortint is 0.

****Syntax :**** `shortint variable_name;`  

****Example :**** `shortint shortint_data;`

The below figure shows the output of shortint data type.

![shortint](https://user-images.githubusercontent.com/110448382/186825172-17bb35a1-c1a4-4071-ad9f-6e45e9011b8f.png)

                                       Figure.7. shortint output

---

## 8. int 

int is 2-state data type which is used most often testbenches. It can be either 0 or 1 which represent a 32-bit signed integer. Default value of int is 0.

****Syntax :**** `int variable_name;`  

****Example :**** `int int_data;`

The below figure shows the output of int data type.

![int](https://user-images.githubusercontent.com/110448382/186825210-010b32ee-95c4-4c6e-b638-9f81ec703812.png)

                                      Figure.8.int output

---

## 9. longint 

longint is 2-state data type. It can be either 0 or 1 which represent a 64-bit signed integer. Default value of longint is 0.

****Syntax :**** `longint variable_name;`  

****Example :**** `longint longint_data;`

The below figure shows the output of longint data type.

![longint](https://user-images.githubusercontent.com/110448382/186825249-c7470eb9-2738-4218-8d16-ce9634cd5c31.png)

                                        Figure.9. longint output

---

# enum

Enumerated data types defines a set of named values.

****Syntax**** : `enum enum_base_type(optional) { <enum_name_declaration> = constant_expr(optional)...} <enum_type_identifier>;`  

****Example :**** `enum {monday, tuesday, wednesday, thursday, friday, saturday, sunday} days;`

* An enumerated type is stored as type ‘int’ unless specified as something else.
* This type automatically gives a unique value to every name in the list.
* Values default to the ‘int’ type starting at 0 and then incrementing by 1.
* If a value is not specified for a name, it gets the value of the previous name in the list incremented by 1.

In the below figure output of default value of enum. 
  
![default_enum](https://user-images.githubusercontent.com/110448382/186869397-d54b85a0-2276-4c1a-98a1-bc23bfef1ea4.png)

                                   Figure.1. Output of enum default value

In the below figure output of set value of enum.  

![set_enum](https://user-images.githubusercontent.com/110448382/186869460-cf12764a-49ec-4379-a174-7b3870a0c6e0.png)

                                   Figure.2. Output of set enum value

---


****enum method :****

sl.no|Method | Description
-- |-- | --
1|first() | returns the value of the first member of the enumeration
2|last() | returns the value of the last member of the enumeration
3|next() | returns the value of next member of the enumeration
4|prev() | returns the value of previous member of the enumeration
5|num() | returns the number of elements in the given enumeration
6|name() | returns the string representation of the given enumeration value

                                          Tabular column.1. enum methods 

---

### enumerated types data type typedef

In typedef a type name can be given so that the same type can be used in many places.  

****Syntax**** : `typedef enum enum_base_type(optional) { <enum_name_declaration> = constant_expr(optional)...} <enum_type_identifier>;`  

****Example :**** `typedef enum {monday, tuesday, wednesday, thursday, friday, saturday, sunday} week;`  
`week = day;`  

In below figure declare typedef type and output using enum methods.

![typedef_enum](https://user-images.githubusercontent.com/110448382/186874037-c29e2317-5854-4fd9-a859-df544365b10a.png)

                                   Figure.3. Output of typedef enum using enum method

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

