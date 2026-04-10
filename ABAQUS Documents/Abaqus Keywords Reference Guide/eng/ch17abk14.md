# *RELEASE







### *RELEASERelease rotational degrees of freedom at one or both ends of a beam element.

This option is used to release a rotational degree of freedom or a combination of rotational degrees of freedom at one or both ends of a beam element.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Kinematic coupling constraints," Section 35.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pkinematiccoupling)
- ["Element end release," Section 35.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-prelease)

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to prescribe the released degrees of freedom: **

**First line:**

Repeat this data line as often as necessary to specify the rotational degrees of freedom to be released for different elements and element ends.




