# *PSD-DEFINITION







### *PSD-DEFINITIONDefine a cross-spectral density frequency function for random response loading.

This option is used to define a frequency function for reference in the [*CORRELATION](ch03abk77.md) option to define the frequency dependence of the random loading in the [*RANDOM RESPONSE](ch17abk07.md) analysis procedure.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)
- ["UPSD," Section 1.1.48 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uupsd)
- [*CORRELATION](ch03abk77.md)
- [*RANDOM RESPONSE](ch17abk07.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this frequency function.

### **Optional parameters: **

DB REFERENCE

Set this parameter equal to the reference power value, in (load units)2. This parameter is required when the frequency function is given in decibel units (TYPE=DB).

G

Set this parameter equal to the reference gravity acceleration; for example, 9.81 m/s2. The default is G=1.0. This parameter can be used only with TYPE=BASE.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

TYPE

Set TYPE=BASE if this frequency function will be used to define a base motion.

Set TYPE=FORCE (default) if this frequency function is given directly in power units.

Set TYPE=DB if this frequency function is defined in decibel units (see below). This option cannot be used with the USER parameter.

USER

Include this parameter if the frequency function is defined in user subroutine [`UPSD`](../sub/sub-link.md#sub-xsl-upsd). If this parameter is included, no data lines are needed.

### **Data lines for TYPE=BASE or TYPE=FORCE: **

**First line:**

Repeat this data line as often as necessary to define the frequency function.

### **Data lines for TYPE=DB: **

**First line:**

Repeat this data line as often as necessary to define the frequency function in decibels.

### **To define the frequency function by a user subroutine (USER parameter included): **

No data lines are used with this option if the USER parameter is specified. Instead, user subroutine [`UPSD`](../sub/sub-link.md#sub-xsl-upsd) must be used to define the frequency function.




