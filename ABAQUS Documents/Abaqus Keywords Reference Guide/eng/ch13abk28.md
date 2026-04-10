# *MONITOR







### *MONITORDefine a degree of freedom to monitor.

This option is used to choose a node and degree of freedom to monitor the progress of the solution in the status file. In Abaqus/Standard the information will also be written to the message file.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Required parameters: **

DOF

Set this parameter equal to the degree of freedom to be monitored at the node. In an Abaqus/Explicit analysis the degree of freedom will be in the global coordinate system. If the [*TRANSFORM](ch19abk11.md) option is used at the node in an Abaqus/Standard analysis, the degree of freedom is in the local, transformed, system.

NODE

Set this parameter equal to either the node number to be monitored or the name of a node set containing the node to be monitored. If the name of a node set is chosen, the node set must contain exactly one node.

### **Optional parameter: **

FREQUENCY

This parameter applies only to Abaqus/Standard analyses.

This parameter will only affect output to the message file. Set this parameter equal to the output frequency in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

**There are no data lines associated with this option.**



