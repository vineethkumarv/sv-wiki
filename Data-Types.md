# Data Types

In Verilog, all the data types were of 4-state, i.e., it could represent 0, 1, X and Z. However, in the case of test benches, these 4-state variables were not required. For example, to count the number of packets, we would require a 2-state variable. Thus, System Verilog introduces a new class of variables of 2-states, i.e., 0 and 1. 

## New Variables in System Verilog
### 1) Logic


