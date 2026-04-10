# *ELSET







### *ELSETAssign elements to an element set.

This option is used to assign elements to an element set.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

**Abaqus/CAE: **Set toolset

##### **Reference:**

- ["Element definition," Section 2.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ielement)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set to which the elements will be assigned.

### **Optional parameters: **

GENERATE

If this parameter is included, each data line should give a first element, ![](../graphics/key_eqn00173.gif); a last element, ![](../graphics/key_eqn00655.gif); and the increment in element numbers between these elements, *i*. Then, all elements going from ![](../graphics/key_eqn00173.gif) to ![](../graphics/key_eqn00655.gif) in steps of *i* will be added to the set. *i* must be an integer such that ![](../graphics/key_eqn00656.gif) is a whole number (not a fraction).

INSTANCE

Set this parameter equal to the name of the part instance that contains the elements listed on the data line. This parameter can be used only at the assembly level and is intended to be used as a shortcut to the naming convention. It can be used only in a model defined in terms of an assembly of part instances.

INTERNAL

Abaqus/CAE uses the INTERNAL parameter to identify sets that are created internally. The INTERNAL parameter is used only in models defined in terms of an assembly of part instances. The default is to omit the INTERNAL parameter.

UNSORTED

If this parameter is included, the elements in this element set will be assigned to the set (or added to the set if it already exists) in the order in which they are given.

If this parameter is omitted, the elements in the set are sorted into ascending order of their element numbers, with duplicates eliminated.

### **Data lines if the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data lines if the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary.




