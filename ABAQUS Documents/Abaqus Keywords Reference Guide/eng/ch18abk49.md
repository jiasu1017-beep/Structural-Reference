# *SURFACE FLAW







### *SURFACE FLAWDefine geometry of surface flaws.

This option is used with line spring elements to define the geometry of the part-through crack of the shell.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **Reference:**

- ["Line spring elements for modeling part-through cracks in shells," Section 32.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-elinespring)

### **Required parameter: **

SIDE

Set SIDE=POSITIVE or SIDE=NEGATIVE to indicate which surface is cracked.

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to define the flaw: **

**First line:**

Repeat this data line as often as necessary to define the crack depth at all nodal locations along the crack.




