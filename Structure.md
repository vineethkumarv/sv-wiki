## Structure  

 A structure contains different data types with different sizes which grouped under one single structure name. Structure  is originally unpacked form by default, but we can use 'packed' keyword  for converting  into packed structure. Structure is different from normal array because array uses only same type of elements with sizes whereas structure uses different data types. The unpacked structure declared using 'struct' keyword.    
 
The below figure shows different types of structures in System Verilog.
![image](https://user-images.githubusercontent.com/110484152/186200139-5258a878-c717-4c94-8fa4-33a53a8d7680.png)  

                                                Fig 1: Structure Diagram  

## Unpacked Structure  
 
Unpacked structure is the default structure syntax and is same as normal structure. The different variables holds different data inside the structure known as members of the structure. Structure members were treated as independent variables. when we want to assign values to  the members of structure, then use 'structure name. variable'.    

****Assignments To Struct Members:****

structure name = '{value1, value2, value3};   

**** Alternate Method to assign values:****  
 
 structure name = '{variable1 : value1 , variable2 : value2 , variable 3 : value3};  
This method gives initialization done in one step. The variable and value can be separated by a colon '.' .


 **Syntax:**

`struct{`    
        `list of  different types of variables with sizes`      
      `} structure name;`    

**Example:**    
 
`struct{` 
       `string name;`   
       `int salary;`  
       `byte id;`  
       `} employee;`    



 **Output:**   
   
The below output shows the unpacked structure.
![s1](https://user-images.githubusercontent.com/110484152/186596674-18bb7ee5-7000-4f59-aa2b-8909b0c94c66.png)

                                                      Fig 2: Unpacked structure  

The above output illustrates that the unpacked structure contains the different datatypes like string, int, byte etc. The string must be initialised within double quotes only. The variables like int , byte can be assign the value itself



## **Packed structure**  
 
Packed structure can explicitly done using packed keyword. It stores all members of structures in the form of contiguous form in a specified order.
In RTL code, a packed structure is treated as a single vector and each data type in the structure is represented as a bit field. The whole structure is packed together in memory without gaps. Only packed data types like bit , logic  and integer data types are also  allowed to use  in a packed structure.

Note: Structure cannot be packed if it cannot be represented as a vector.     

 **Syntax:**  

`typedef struct packed{`  
`list of  different types of variables with sizes`  
`} structure name;`   

 **Example:**     

`typedef struct packed{`  
`byte id;`  
`bit[7:0]experience;`   
`logic[15:0]salary;`  
`}employee_ details;` 

 **Output:**     

The below output shows that output of packed structure  
![ps1](https://user-images.githubusercontent.com/110484152/186596534-8471a1dd-bdf0-401f-bfc7-2ecedd59157a.png)  

                                            Fig 3: Packed structure  

The above output illustrates the output of packed structure. It contains the different datatypes like bit , logic . We can assign values and  display as output. Here we cannot  use string dataype inside the packed structure because string cannot be treated as single vector. It will show compile error.   


----


# **Typedef**    

Typedef used to create new identifiers from longer datatype specification. It  is similar to alias command. Typedef uses mainly in complex testbenches in System Verilog because it replaces the longer datatypes like int(unsigned longint, signed shortint), byte ,bit[7:0],logic[7:0] with identifiers in the code. Typedef uses in Class, Structure and  Enumeration to  make the datatype declarations  easier.  
  
 **Syntax:**  

`typedef <base_type> <size> <type_name>;`  

 
## **Typedef in Class**   

The main use of Typedef in class is that sometimes we use class variable before the declaration of the class itself. At that time it will cause some compile errors to the code. So avoid that compile errors , we can use 'typedef class variable' before the declaration of class itself.   
  
 **Syntax:**  

`typedef class class_name;`

 **Example:**    

`typedef class fruit2;`   
`class fruit1;`    
`fruit2 f;`  
`endclass` 

`class fruit2`    
`fruit1 f;`  
`endclass`  

 **Output:**    

The below figure shows that output of typedef with class.
![typedef class](https://user-images.githubusercontent.com/110484152/186602737-1d67bede-f186-4483-822b-cc8d808c1f21.png)  

                                                   Fig 1 : Typedef with class  

The above example and output shows that how typedef avoids the compiler error in class1 because class2 declaration is not done  at that time. If we didn't use 'typdef class2' at the beginning , it will show some compiler error. It will display the text given inside the $display.

## **Typedef in Structure**  

Without Typedef, Structure may happen some compile errors in large complex testbenches. Typedef also provide declarations make more easier.  

 **Syntax:**     

`typedef struct {`   
         `datatype name;`  
         `datatype name;`  
         `}structure_name;`  

 **Example:**   
 
`typedef struct{`  
`string name;`  
`byte id;`   
`longint age;`   
`} personal_ details;` 

 **Output:**    

The below figure shows the output of typedef with structure datatype.
![12](https://user-images.githubusercontent.com/110484152/186636386-2301edc3-eda9-498c-b038-84e4c3de68a4.png)  

                                                    Fig 2: Typedef with structure  

The above output shows that typedef in structure decreases the usage of longer datatypes by creating new variable. We can see that in example 'longint' datatype changed to 'age' ,it is a new variable that is created by using typedef in structure.   
## **Typedef in Enumeration**   

Typedef uses for when we need more than one variable to share the same enumeration values. Without Typedef we will get syntax error. Enumeration datatype create new variable for all values.
 
 **Syntax:**    

 `typedef enum { values } <type_ name>;`

 **Example:**    

`typedef enum {RORITO,FLAIRFX,REYNOLDS} <e_ pen>;`

 **Output:**    

The below figure shows the typedef with 'enumeration datatype  
![typeenum](https://user-images.githubusercontent.com/110484152/186602985-64dd1698-8a5d-4951-9a30-523acc0ad1bc.png)  

                                             Fig 3 : Typedef with Enumeration 

The above output shows that enum datatype with typedef .If we didn't use typedef with enumeration datatype, it will show syntax error. The output shows that enumeration datatype created a new variable 'e_ pen' and initialize a variable 'pen'. After this, choose one value and assign to 'pen'. It will display the assigned value.   
