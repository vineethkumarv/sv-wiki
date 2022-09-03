# **System Verilog Interview Questions**    

**1.What is the difference between a reg, wire and logic in System Verilog?**

* The reg and wire are two data types that existed from Verilog, whereas logic is a new data type that was introduced in System Verilog.   
* A wire is a data type that  model physical wires to connect two elements. Wires can only be driven by continuous assignment statement and cannot hold onto value if not driven. Wires can hence only be used to model combinational logic.  
* A reg is a data type that can model a storage element or a state. They need to be driven by an always block and cannot be driven by continuous assignment statement. A reg can be used to model both sequential and combinational logic.  
* A logic is a new data type in System Verilog that can be used to model both wires and state information (reg). It also is a 4 state variable and hence can hold 0, 1, x and z values. If a wire is declared as a logic (wire logic), then it can be used to model multiple drivers and the last assignment will take the value.    

**2.What is the difference between a bit and logic data type?**  

* The bit is a 2-state data type that can take only values 0 and 1, while logic is a 4-state data type which can take values 0, 1, x, and z.
* 2-state variables will help in a small simulation speed up but should not be used if it is used to drive or sample signals from RTL design in which uninitialized and unknown values will be missed.    

**3. What is the difference between logic[7:0] and byte variable in System Verilog?**

* The 'byte' is a signed variable which means it can only be used to count values till 127.
* A logic[7:0] variable can be used for an unsigned 8 bit variable that can count up to 255.  

**4.What is the difference between a struct and union in System Verilog?**

A structure represents a collection of data types that can be referenced as a whole, or the individual data types that make up the structure can be 
referenced by name.
For example:
we have a struct defined called instruction_ s that groups a 24 bit address field and an 8 bit opcode field.

  typedef struct {  
  bit [7:0] opcode;  
  bit [23:0] addr;  
  } instruction_ s  
  instruction_ s current_ instruction;  
  current_ instruction. addr =’h100;

The instruction_ s struct can be referenced together or individual members can be accessed. The total memory allocated would be the sum of memory needed for all the data types. Hence in above example, the current _instruction struct would take a total memory of 32 bits (24 bit address and 8 bit opcode) A union is a data type which can be accessed using one and only one of the named member data type. Unlike struct you cannot access all member data types together. The memory allocated for the union would be the maximum of the memory needed for the member data types. Unions are normally useful if you want to model a hardware resource like register that can store values of different types. For example: if a register can store an integer and a real values, you can define a union as follows:

 typedef union {  
 int data;  
 real f_data;  
 } state_u;  
 state_ u reg_ state;  
 reg_state.f_ data = ‘hFFFF_FFFF_FFFF_FFFF;  
 $display(“ int_ data =%h“, reg_ state.data);  

In this example, the union state_u can either hold a 32 bit integer data or it can hold 64 bit real data. Hence, the memory allocated for the union reg_state will be 64 bits (bigger of the two data types). Since, there is shared memory for all member data types, in above example, if we assign a 64 bit value to reg_state.f_data, we will be also able to reference the 32 bit of same using the other data type.  

**7.What is the difference between a packed array and an unpacked array?**

A packed array represents a contiguous set of bits while an unpacked array need not be represented as a contiguous set of bits. In terms of a difference in declarations, the following is how a packed and unpacked array is declared.

bit [7:0] data ; // packed array of scalar bit types  
real latency [7:0]; // unpacked array of real types  
Packed arrays can be made of only the single bit data types (bit, logic, reg) or enumerated types.  

logic[31:0] addr; //packed array of logic type  
Unpacked arrays can be made of any data type.  

class record_c;  
record_c table[7:0]; //unpacked array of record objects  

**8.Given a dynamic array of size 100, how can the array be re-sized to hold 200 elements while the lower 100 elements are preserved as original?**

A dynamic array needs memory allocation using new[] to hold elements. Here is an example with an integer array that grows from an initial size of 100 elements to 200 elements.    

 integer addr[]; // Declare the dynamic array.  
 addr = new[100]; // Create a 100-element array.  
 ………  
 // Double the array size, preserving previous values.  
 addr = new[200](addr);

**9.what is typedef in System Verilog?**

We use the typedef keyword to create a new data type in our System Verilog code. In most cases, we simply use a typedef to assign a name to a type declaration which we want to use in multiple places in our code. This is useful as we can create quite complex data types in System Verilog.  

**10.what is packed structure in System Verilog?**  

A packed structure like a packed array can be thought of as a single dimension memory or a vector. In a packed array, this vector is divided into equal size partitions which can sometimes be inefficient as often data would be of different lengths. Packed structure on the other hand divides the vector into unequal size partitions providing more efficient packing of data.  

**11.what is the significance of typedef in system Verilog?**  

We use the typedef keyword to create a new data type in our System Verilog code. In most cases, we simply use a typedef to assign a name to a type declaration which we want to use in multiple places in our code. This is useful as we can create quite complex data types in System Verilog.  

**12.What is dynamic array explain with example?**

 Dynamic Array:   
 Example:  

 int dyn_arr [];  
 initial  
 begin  
 dyn_arr = new[10];        //Allocated 10 elements   
 end
 
Using new[] operator, we can allocate elements how much we want. So it will use memory space efficiently because  it will allocate memory only run time.  

**13.What is associative array ?**

* It is also allocated during run time.
* This is the array, user need when data is sparse.
* It is used when we don’t have to allocate contiguous collection of data, or data in a proper sequence or index.
* Indexing is not regular, can be accessed using indexing like integer or string type or any scalar.    

**14.What is Queue in system Verilog?**

* Queue is a variable size, ordered collection of Homogenous Data.
* It is flexible, as it is variable in size and analogous to an 1-dimensional Unpacked array that can shrink & grow automatically and can be of size 
  zero.
* The main advantage of queue over dynamic array is that, we don’t need new[] operator to allocate storage space for a queue.
* The other advantages of queue over dynamic array is that we can manipulate the queue using various queue methods like: push, pop, delete, insert, 
  size.  

**15.What is associative array Methods?**    

* function int num()
  * Returns the number of entries in the array, if empty returns 0  

* function void delete( [input index] )
  * Index is optional  
  * If index is specified, deletes the item at the specified index
  * If index is not specified the all elements in the array are removed
 
* function int exists ( input index );  
  * Checks if an element exists at the specified index within the given array.
  *   Returns 1 if the element exists, otherwise it returns 0  

* function int first( ref index )
  * Assigns to the given index variable the value of the first (smallest) index in the associative array
  * It returns 0 if the array is empty, and 1 otherwise

* function int last( ref index )  

 *  Assigns to the given index variable the value of the last (largest) index in the associative array    
  
* function int next( ref index );  

  * finds the entry whose index is greater than the given index. If there is a next entry, the index variable is assigned the index of the next entry, 
     and  the function returns 1.
  * Otherwise, index is unchanged, and the function returns 0  

* function int prev( ref index );   
 
  * finds the entry whose index is smaller than the given index. If there is a previous entry, the index variable is assigned the index of the previous 
   entry, and the function returns 1
  * Otherwise, the index is unchanged, and the function returns 0 






 