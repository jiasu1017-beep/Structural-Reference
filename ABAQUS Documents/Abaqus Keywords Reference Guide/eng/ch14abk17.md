# *NSET







### *NSETAssign nodes to a node set.

This option assigns nodes to a node set.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

**Abaqus/CAE: **Set toolset

##### **Reference:**

- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

### **Required parameter: **

NSET

Set this parameter equal to the name of the node set to which the nodes will be assigned.

### **Optional parameters: **

ELSET

Set this parameter equal to the name of a previously defined element set. The nodes that define the elements that belong to this element set at the time this option is encountered will be assigned to the node set specified. The UNSORTED parameter cannot be used with this parameter.

The ELSET and GENERATE parameters are mutually exclusive.

GENERATE

If this parameter is included, each data line should give a first node, ![](../graphics/key_eqn00707.gif); a last node; ![](../graphics/key_eqn00708.gif); and the increment in node numbers between these nodes, *i*. Then, all nodes going from ![](../graphics/key_eqn00707.gif) to ![](../graphics/key_eqn00708.gif) in steps of *i* will be added to the set. *i* must be an integer such that ![](../graphics/key_eqn00926.gif) is a whole number (not a fraction). 

The ELSET and GENERATE parameters are mutually exclusive.

INSTANCE

Set this parameter equal to the name of the part instance that contains the nodes listed on the data line. This parameter can be used only at the assembly level and is intended to be used as a shortcut to the naming convention. It can be used only in a model defined in terms of an assembly of part instances.

INTERNAL

Abaqus/CAE uses the INTERNAL parameter to identify sets that are created internally. The INTERNAL parameter is used only in models defined in terms of an assembly of part instances. The default is to omit the INTERNAL parameter.

UNSORTED

If this parameter is included, the nodes in this node set will be assigned to the set (or added to the set if it already exists) in the order in which they are given. This parameter will be ignored if the ELSET parameter is used.

If this parameter is omitted, the nodes in the set are sorted into ascending order of their node numbers, with duplicates eliminated.

### **Data lines if the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data lines if the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary.

### **There are no data lines when the ELSET parameter is specified. **




