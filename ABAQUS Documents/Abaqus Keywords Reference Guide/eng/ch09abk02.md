# *IMPEDANCE PROPERTY







### *IMPEDANCE PROPERTYDefine the impedance parameters for an acoustic medium boundary.

This option is used to define the proportionality factors between the pressure and the normal components of surface displacement and velocity in acoustic analysis. The [*IMPEDANCE PROPERTY](ch09abk02.md) option must be used in conjunction with the [*IMPEDANCE](ch09abk01.md) or [*SIMPEDANCE](ch18abk17.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*IMPEDANCE](ch09abk01.md)
- [*SIMPEDANCE](ch18abk17.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the impedance property on the [*IMPEDANCE](ch09abk01.md) or [*SIMPEDANCE](ch18abk17.md) option.

### **Optional parameters: **

DATA

Set DATA=ADMITTANCE (default) to specify an impedance using a table of admittance values.

Set DATA=IMPEDANCE to specify an impedance using a table of real and imaginary parts of the impedance.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to define an impedance using DATA=ADMITTANCE (default): **

**First line:**

Repeat this data line as often as necessary in Abaqus/Standard to describe the variation of the coefficients with frequency. Only the first line entered will be used in direct-integration procedures.

### **Data lines to define an impedance using DATA=IMPEDANCE: **

**First line:**

Repeat this data line as often as necessary in Abaqus/Standard to describe the variation of the coefficients with frequency. Only the first line entered will be used in direct-integration procedures.




