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

![typedef class](https://user-images.githubusercontent.com/110484152/187588716-d102f765-7b5e-4d28-824e-7f6da953e085.png)
                                                   Fig 1 : Typedef with class  

The above example and output shows that how typedef avoids the compiler error in class1 because class2 declaration is not done  at that time. If we didn't use 'typdef class2' at the beginning , it will show some compiler error. It will display the text given inside the $display.  


Github lab code link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/classtypedef/classtypedef.sv  

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/classtypedef/classtypedef.log  

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
`} personal_ details_s;` 

 **Output:**    

The below figure shows the output of typedef with structure datatype.
![typestruct](https://user-images.githubusercontent.com/110484152/187587821-78efe5d6-c0f7-433c-a014-eee8cee3dcd7.png)  

                                                 Fig 2: Typedef with structure  

The above output shows that typedef in structure decreases the usage of longer datatypes by creating new variable. We can see that in example 'longint' datatype changed to 'age' ,it is a new variable that is created by using typedef in structure.   

Github lab code link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/structtypedef/structtypedef.sv  

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/structtypedef/structtypedef.log
 
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

Github lab code link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/enumtypedef/enumtypedef.sv  

Github lab output link:https://github.com/muneeb-mbytes/SystemVerilog_Course/blob/b7_team_kachori/data_type/typedef/enumtypedef/enumtypedef.log

