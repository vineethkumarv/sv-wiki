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
• Active regions (Active, Inactive and NBA regions).  
Regions that are designed to implement correct verification execution:  
• Preponed, Reactive regions (Reactive, Re-Inactive, Re-NBA) and Postponed regions.  
Regions that are designed to implement concurrent assertion checking:  
• Preponed, Observed, and Reactive regions.  
Region that should be avoided:  
• Inactive region.  

Let's discuss about all the regions of System Verilog  

## 1. Active Region set  

This Active region set includes 
**i. Active region**
**ii. Inactive region** and 
**iii. NBA region.**

The Active region set is used to schedule blocking and non-blocking assignments included in the module.  
All tasks and functions called from a module also scheduled in the active region set.  
The Active region set is used to schedule the RTL and behavioral code.

### i. Active region

The Active region holds the current active region set events being evaluated and can be processed in any order.  

The principal function of this region is to evaluate and execute all current module activity in any order:  

• Execute all module blocking assignments.  
• Execute all module continuous assignments.  
• Evaluate the Right-Hand-Side (RHS) of all non-blocking assignments and schedule updates into the NBA region.  
• Evaluate inputs and update outputs of Verilog primitives.  
• Execute the $display and $finish commands.  

### ii. Inactive regions

The Inactive region holds the events to be evaluated after all the Active events are processed.  
Most engineers are continue to use #0 assignments are trying to defeat a race condition that might exist in their code due to assignments  
made to the same variable from more than one always block.  
If events are being executed in the active region set, an explicit #0 delay control requires the process to be suspended and an event to be scheduled into the Inactive region of the current time slot so that the process can be resumed in the next Inactive to Active iteration.  
Engineers that follow good coding practices will have no need for #0 RTL assignments and hence, the Inactive region is unused.  

### iii. NBA region

The principal function of this region is to execute the updates to the Left-Hand-Side (LHS) variables that were scheduled in the Active region for all currently executing non-blocking assignments.  
The NBA (non-blocking assignment update) region holds the events to be evaluated after all the Inactive events are processed.  
If events are being executed in the active region set, a non-blocking assignment creates an event in the NBA region scheduled for the current or a later simulation time.  

## 2. Re-Active region set

This Re-Active region set includes 
**i. Re-Active region**
**ii. Re-Inactive region** and 
**iii. Re-NBA region.**

The Reactive region holds the current reactive region set events being evaluated and can be processed in any order.
The code specified by blocking assignments in checkers, program blocks and the code in action blocks of concurrent assertions are scheduled 
in the Reactive region.  
The reactive region set is used to schedule blocking assignments, #0 blocking assignments and non-blocking assignments included in program code. Any task or function called from a program is also scheduled into the reactive set event regions.  
The intended purpose of the reactive region set is to schedule testbench stimulus drivers and testbench verification checking in the same time slot after RTL code has settled to a semi-steady state.  



--------------------------------------------- Race aviodance ---------------------------------------------  

Race avoidance:

Sunburst Design Race Avoidance Guideline #3 dictates that all RTL combinational logic
modeled using an always block should be coded using blocking assignments to ensure that
combinational logic execute

This region is where #0 blocking assignments are scheduled and per Sunburst
Design Race Avoidance Guideline #8, engineers should not make #0 RTL procedural
assignments3

, which is a violation of Sunburst Design Race Avoidance Guideline #6.

Sunburst Design Race Avoidance Guideline #1 dictates that all RTL clocked logic modeled
using an always block should be coded using nonblocking assignments to ensure that the
sequential logic will execute in the NBA region and correctly model the pipelined nature of
sequential elements
