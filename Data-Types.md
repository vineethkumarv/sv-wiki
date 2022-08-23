# Data Types

In Verilog, all the data types were of 4-state, i.e., it could represent 0, 1, X and Z. However, in the case of test benches, these 4-state variables were not required. For example, to count the number of packets, we would require a 2-state variable. Thus, System Verilog introduces a new class of variables of 2-states, i.e., 0 and 1. 

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


## New Variables in System Verilog
### 1) Logic


