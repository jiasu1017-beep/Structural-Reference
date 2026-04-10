# *RETAINED NODAL DOFS







### *RETAINED NODAL DOFSSpecify the degrees of freedom that are to be retained as external to a substructure.

This option is used to list degrees of freedom that are to be retained as external degrees of freedom on the substructure. It can be used only in a [*SUBSTRUCTURE GENERATE](ch18abk42.md) analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### **Optional parameter: **

SORTED

Set SORTED=NO to prevent the retained nodes from being sorted. The ordering of the nodes when using a substructure is then the same as the ordering used when specifying the retained nodes. The default is SORTED=YES, the retained nodes are sorted into ascending numerical order.

### **Data lines to define the retained degrees of freedom: **

**First line:**

If only the node number or node set label is given, all degrees of freedom will be retained.

Repeat this data line as often as necessary to list all degrees of freedom to be retained.




