# *NODAL ENERGY RATE







### *NODAL ENERGY RATEDefine critical energy release rates at nodes.

This option is used to define variable critical energy release rates on a nodal basis. The critical energy release rate data defined with this option is ignored unless the NODAL ENERGY RATE  parameter is included on the [*FRACTURE CRITERION](ch06abk33.md), TYPE=VCCT option or the [*FRACTURE CRITERION](ch06abk33.md), TYPE=FATIGUE option. 

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Crack propagation analysis," Section 11.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acrackpropagation)
- [*FRACTURE CRITERION](ch06abk33.md)

### **Optional parameters: **

GENERATE

Include this parameter to interpolate the critical energy release rates between two bounding nodes or node sets. The critical energy release rates for the bounding nodes or node sets must have been defined earlier. If the node sets do not have the same number of nodes, the extra nodes in the longer set are ignored.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines when the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary to define the variation in critical energy release rates.

### **Data lines when the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary to define the variation in critical energy release rates.




