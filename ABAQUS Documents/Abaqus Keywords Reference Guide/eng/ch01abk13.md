# *AQUA







### *AQUADefine fluid variables for use in loading immersed beam-type structures.

This option is used to define the fluid properties and steady-current velocity.

**Product: **Abaqus/Aqua  

**Type: **Model data  

**Level: **Model  

##### **Reference:**

- ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua)

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to define fluid properties and a steady current: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define the steady current velocity as a function of elevation and spatial coordinates. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for a description of how to define a property as a function of multiple independent variables.




