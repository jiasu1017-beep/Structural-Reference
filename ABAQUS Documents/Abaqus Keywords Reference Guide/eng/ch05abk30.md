# *EQUATION







### *EQUATIONDefine linear multi-point constraints.

This option is used to define linear multi-point constraints in the form of an equation.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Linear constraint equations," Section 35.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pequation)

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line. 

### **Data lines to define an equation: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define all of the terms of the equation. No more than four terms can be defined on a line. To define another constraint, repeat the entire set of data lines.




