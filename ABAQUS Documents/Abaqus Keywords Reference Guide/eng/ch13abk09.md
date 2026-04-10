# *MATRIX







### *MATRIXRead in the stiffness or mass matrix for a linear user element.

This option can be used only in conjunction with the [*USER ELEMENT](ch20abk07.md), LINEAR option. It is used to read in the stiffness or mass matrix for the user element. It can be used once if only a stiffness or mass is required or twice to give both matrices.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance,  Model  

##### **References:**

- ["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)
- [*USER ELEMENT](ch20abk07.md)

### **Required parameter: **

TYPE

Set TYPE=MASS to define the mass matrix. Set TYPE=STIFFNESS to define the stiffness matrix.

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file from which the data lines are to be read. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to define the matrix: **

**First line:**

Repeat this data line as often as necessary.




