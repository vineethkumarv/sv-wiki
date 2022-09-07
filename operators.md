**Operators** : 

****Operators****  :  

![opppp](https://user-images.githubusercontent.com/106074838/188847440-ad11ced1-9375-4e1e-956e-b5b4eab2d7b9.png)    

                         Figure.1 operators 
There  



**1. Arithmetic Operators**    
We use arithmetic operators to perform basic mathematic functions on our variables. These operators should already be familiar as they are mostly replications of common mathematic symbols.  

**The table below shows the full list of arithmetic operators in SystemVerilog.**    
![airthmatic_1](https://user-images.githubusercontent.com/106074838/188830091-fab594b8-522f-4c59-8fad-6268427aab03.PNG)  

The below figure shows the output of the Arithmetic operator screenshot  
![Untitled Diagram drawio (2)](https://user-images.githubusercontent.com/106074838/188851432-89a890f2-25d9-42c2-9abe-dbe0d3398503.png)    

                       Figure.2. the output of the arithmetic operator. 


for Better understanding go through this code  
**GitHub lab code link:**   
    

**GitHub lab output link:**   
  

***
2.****Relational operator****

**Relation operator cheat sheet**

Operator | Description
-- | --
a < b | a less than b
a > b | a greater than b
a <= b | a less than or equal to b
a >= b | a greater than or equal to b


These operators compare operands and result in a 1-bit scalar Boolean value.  
* 0 if the relation is false   
* 1 if the relation is true   
* x if any of the operands has unknown x bits   


****Example:****  
Consider, a = 111     
          b = 101

*  **a < b**:Here a is greater than b, the relation is false, so the result is 0.


* **a > b**:Here a is greater than b,  the relation is true, so the result is 1.

*  **a <= b**:Here a is greater than b, the relation is false, so the result is 0.


*  **a >= b**:Here a is greater than b,  the relation is true, so the result is 1.

![relational](https://user-images.githubusercontent.com/106074838/188854561-7c933302-bbc5-471c-99a3-ff545eac4ba6.png)  

              Figure.3. the output of the relation operator. 

**GitHub lab code link**     

**GitHub lab output link**  

***

3.**Equality operator:**  

The equality operators are used to compare expressions. If the comparison fails, then the result will be 0, otherwise, it will be 1.
There are two types of Equality operators.   
* Case Equality   
* Logical Equality.  

**Equality operator cheat sheet**

Operator | Description
-- | --
a === b | a equal to b, including x and z (Case equality)
a !== b | a not equal to b, including x and z (Case inequality)
a == b | a equal to b, the result may be unknown (logical equality)
a != b | a not equal to b, the result may be unknown (logical equality)
  
* If both operands of logical equality (==) or logical inequality (!=) contain unknown (x) or a high-impedance (z) value, then the result of the comparison will be unknown (x). Otherwise, it will be true or false.  

* If operands of case equality (===) or case inequality (!==) contain unknown (x) or a high-impedance (z) value, then the result will be calculated bit by bit.  
 
****Example:****  
Consider, a = 111     
          b = 101
*  **a == b**: Here we perform the logical equality of a,b, the result is zero when both numbers are the same then the result is 1.  
*  **a != b**: Here we perform the logical inequality of a,b the result is 1 when both numbers are the same then the result is 0.  
*  **a === b**: Here we perform the case equality of a,b the result is zero when both numbers are the same then the result is 1.  
*  **a!=== b**: Here we perform the case inequality of a,b the result is 1 when both numbers are the same then the result is 0.  
   
 
![equality](https://user-images.githubusercontent.com/106074838/188873316-cbe43fc7-65f3-4007-a299-2cb25b8e3e90.png)  

                   Figure.4. the output of the equality operator. 


**GitHub lab code link**     

**GitHub lab output link**  

*** 

**4. Logical Operator**  
The Logical operators are similar to the bit-wise operators   

In the Logical Operator, these expressions return either a 1 (true) or 0 (false).  


There are only three logical operators for better understanding follow the below cheat sheet      

**Logical operator cheat sheet**   
![logical11](https://user-images.githubusercontent.com/106074838/188828213-e579ba4e-f5b2-40ae-aaca-03c14515a34e.PNG)

****Example:****  
Consider, a = 100     
          b = 111
*  **a && b**: Here we performing the Logical AND of a,b, and the result is 1. if any one of the variable values is zero then the result is 0.   
*  **a || b**: Here we performing the Logical OR of a,b, and the result is 1. if all the variable's values are zero then only the result is 0.  
*  **!a **: Here we performing the Logical Not of a and the result is 0. if all variable value is zero then the result is 0. ( just vice versa).  

![logical](https://user-images.githubusercontent.com/106074838/188864090-4a8153c8-fa79-49ca-8fec-ea83d327df8a.png)  

              Figure.4. the output of the Logical operator.  
**GitHub lab code link**     

**GitHub lab output link**  

---
5.**Bitwise operator:**   
We use the bit-wise operators to combine a number of single-bit inputs into a single-bit output.  

**Bitwise operator cheat sheet**  
Operator | Description
-- | --
~ | negation
& | and
\| | inclusive or
^ | exclusive or
^~ or ~^ | exclusive nor (equivalence)


****Example:****  
Consider, a = 100  
b=110  

*  **a & b**: bit-wise and of a,b the result is 100.  
*  **a | b**: bit-wise or of a,b the result is 110.  
*  **a ~& b**: bit-wise nand of a,b the result is 011.  
*  **a ~| b**: bit-wise nor of a,b the result is 001.  
*  **a ^ b**: bit-wise xor of a,b the result is 101.  
*  **a ~^ b**: bit-wise nxor of a,b the result is 010.  



![bitwise](https://user-images.githubusercontent.com/106074838/188878058-9c816249-4770-4567-bbfa-d7c102350f16.png)  

                         Figure.5. the output of the Bitwise operator. 

**GitHub lab code link**     

**GitHub lab output link**  

---
6.


---

8.**Reduction operator:**

**Reduction operator cheat sheet**


Operator | Description
-- | --
& | and
~& | nand
\| | or
~\| | nor
^ | xor
^~ or ~^ | xnor

**GitHub lab code link**     

**GitHub lab output link**  


