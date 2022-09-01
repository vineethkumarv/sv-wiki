# Scheduler schematic:

The scheduling semantics are used to describe the element's behavior and their interaction with each other. This interaction is described for event   execution and its scheduling. It is important to note that Verilog and System Verilog is like a parallel programming language in terms of blocks or  
process executions.

Before going to the regions we have to know about **simulation time** and **time slot**.  

The term **simulation time** is used to refer to the time value maintained by the simulator to model the actual time it would take for the system   description being simulated.  

A **time slot** encompasses all simulation activity that is processed in the event regions for each simulation time. All simulation activity for a   particular simulation time is executed until no further simulation activity remains for that time slot, that is, without advancing the simulation  
time.  
"Note that execution of simulation events within a time slot may require multiple iterations through the simulation event regions for that same time slot."  

## Event regions in verilog:

---------------------- pic of verilog regions -----------------------------------

## Event regions in system verilog:

---------------------- pic of system verilog regions ----------------------------

### Explinations.

Regions that are designed to implement correct RTL functionality:  
• Active regions (Active, Inactive and NBA regions - but avoid Inactive region events).  
Regions that are designed to implement correct verification execution:  
• Preponed, Reactive regions (Reactive, Re-Inactive, Re-NBA) and Postponed regions.  
Regions that are designed to implement concurrent assertion checking:  
• Preponed, Observed, and Reactive regions.  
Region that should be avoided:  
• Inactive region.  

Let's discuss about all the regions of System Verilog  

## 1. Active Region set  

This Active region set includes 
**1. Active region**
**2. Inactive region** and 
**3. NBA region.**

The Active region set is used to schedule blocking and non-blocking assignments included in the module.  
All tasks and functions called from a module also scheduled in the active region set.  
The Active region set is used to schedule the RTL and behavioral code.

### 1.Active region

The Active region holds the current active region set events being evaluated and can be processed in any order.  

The principal function of this region is to evaluate and execute all current module activity in any order:  

• Execute all module blocking assignments.  
• Execute all module continuous assignments.  
• Evaluate the Right-Hand-Side (RHS) of all non-blocking assignments and schedule updates into the NBA region.  
• Evaluate inputs and update outputs of Verilog primitives.  
• Execute the $display and $finish commands.  

--------------------------------------------- Race aviodance ---------------------------------------------
Race avoidance:

Sunburst Design Race Avoidance Guideline #3 dictates that all RTL combinational logic
modeled using an always block should be coded using blocking assignments to ensure that
combinational logic execute
 








