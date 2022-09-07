**Operators** : 

****Operators****  :  


There  



**1. Arithmetic Operators**    
We use arithmetic operators to perform basic mathematic functions on our variables. These operators should already be familiar as they are mostly replications of common mathematic symbols.  

The table below shows the full list of arithmetic operators in SystemVerilog.    
![airthmatic_1](https://user-images.githubusercontent.com/106074838/188830091-fab594b8-522f-4c59-8fad-6268427aab03.PNG)  

The below figure shows the output of the Arithmetic operator screenshot  


for Better understanding go through this code  
**GitHub lab code link**     

**GitHub lab output link**   
  


**2. Logical Operator**  
The Logical operators are similar to the bit-wise operators  
![logical11](https://user-images.githubusercontent.com/106074838/188828213-e579ba4e-f5b2-40ae-aaca-03c14515a34e.PNG)

---

****Relational operator****

**Relation operator cheat sheet**

Operator | Description
-- | --
a < b | a less than b
a > b | a greater than b
a <= b | a less than or equal to b
a >= b | a greater than or equal to b


These operators compare operands and results in a 1-bit scalar Boolean value.  
* 0 if the relation is false   
* 1 if the relation is true   
* x if any of the operands has unknown x bits   



****Example:****  
Consider, a = 111     
          b = 101

*  **a < b** :Here a is greater than b, the relation is false, so the result is 0.


* **a > b** :Here a is greater than b,  the relation is true, so the result is 1.

*  **a <= b** :Here a is greater than b, the relation is false, so the result is 0.


*  **a >= b** :Here a is greater than b,  the relation is true, so the result is 1.

**GitHub lab code link**     

**GitHub lab output link**  


---

**Equality operator:**

**Equality operator cheat sheet**

Operator | Description
-- | --
a === b | a equal to b, including x and z (Case equality)
a !== b | a not equal to b, including x and z (Case inequality)
a == b | a equal to b, result may be unknown (logical equality)
a != b | a not equal to b, result may be unknown (logical equality)

There are two types of Equality operators. Case Equality and Logical Equality.  

* The equality operators are used to compare expressions. If a comparison fails, then the result will be 0, otherwise it will be 1.
* If both operands of logical equality (==) or logical inequality (!=) contain unknown (x) or a high-impedance (z) value, then the result of comparison will be unknown (x). Otherwise it will be true or false.
* If operands of case equality (===) or case inequality (!==) contain unknown (x) or a high-impedance (z) value, then the result will be calculated bit by bit.

**GitHub lab code link**     

**GitHub lab output link**  

---

**Reduction operator:**

**Reduction operator cheat sheet**


Operator | Description
-- | --
& | and
~& | nand
\| | or
~\| | nor
^ | xor
^~ or ~^ | xnor



