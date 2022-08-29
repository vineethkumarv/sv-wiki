## Structure  

 A structure contains different data types with different sizes which grouped under one single structure name. Structure  is originally unpacked form by default, but we can use 'packed' keyword  for converting  into packed structure. Structure is different from normal array because array uses only same type of elements with sizes whereas structure uses different data types. The unpacked structure declared using 'struct' keyword.    
 
The below figure shows different types of structures in System Verilog.
![image](https://user-images.githubusercontent.com/110484152/186200139-5258a878-c717-4c94-8fa4-33a53a8d7680.png)  

                                                Fig 1: Structure Diagram  

## Unpacked Structure  
 
Unpacked structure is the default structure syntax and is same as normal structure. The different variables holds different data inside the structure known as members of the structure. Structure members were treated as independent variables. when we want to assign values to  the members of structure, then use 'structure name. variable'.    

****Assignments To Struct Members:****

structure name = '{value1, value2, value3};   

****Alternate Method to assign values:****  
 
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

Github Lab code link: https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/structure/structn/structn.sv  

Github Lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/structure/structn/structn.log


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

Github lab code link :https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/structure/struct-packed/struct-packed.sv   

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/structure/struct-packed/struct-packed.log


----
# **Union**  

The union is similar to structures while union shares the memory location. The largest datatype size will be the memory size for all members in the union. The 'union' keyword is used for defined for Union. They are two types: Packed Union and Unpacked Union.   

## Unpacked Union  

The unpacked structure use the keyword 'union' keyword. It uses the datatypes like int, byte ,bit, logic .Only the largest datatype size should be taken for the whole union members. In this scenario, sometimes the whole memory space may not be used for all the union members. The value changed for one variable also effects other elements inside the Union. 

## syntax:  

union {  
int data;
byte

## Example:  


## Output:  
   
The below figure shows the output of Unpacked Union.  







## Packed Union    

The Packed Union is defined by 'union packed' keyword. It uses only same type elements with same size. This is one of the limitation of packed Union.


## syntax:  

`typedef union packed  {`  
`list of  different elements`  
`} Union_name;`  

## Example:  

`typedef union packed {` 
`bit [7:0];`
`bit [1:0][3:0];`  
`} abc_u ;`  

## Output:  

The below figure shows that the output of packed union.  







  



  

