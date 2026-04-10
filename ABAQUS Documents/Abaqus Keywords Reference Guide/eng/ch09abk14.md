# *INCLUDE







### *INCLUDEReference an external file containing Abaqus input data.

This option is used to reference an external file containing a portion of the Abaqus input file.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

**Abaqus/CAE: **Several input data options in Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? provide the capability to reference external files; for example, the material editor can read material properties from an ASCII file.

##### **Reference:**

- ["Defining a model in Abaqus," Section 1.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-imodel)

### **Required parameter: **

INPUT

Set this parameter equal to the name of the file containing the input data. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

### **Optional parameter: **

PASSWORD

When the external file is encrypted, set this parameter equal to the file's password. Passwords are case-sensitive.

**There are no data lines associated with this option.**



