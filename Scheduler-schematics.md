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









