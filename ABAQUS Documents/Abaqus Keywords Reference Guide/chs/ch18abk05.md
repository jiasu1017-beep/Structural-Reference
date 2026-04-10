# *SECTION PRINT







### *SECTION PRINTDefine print requests of accumulated quantities on user-defined surface sections.

This option is used to provide tabular output of accumulated quantities associated with a user-defined section. Depending on the analysis type the output may include one or several of the following: the total force, the total moment, the total heat flux, the total current, the total mass flow, or the total pore fluid volume flux associated with the section. This option is not available for eigenfrequency extraction, eigenvalue buckling prediction, complex eigenfrequency extraction, or linear dynamics procedures.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- ["Abaqus/Standard output variable identifiers," Section 4.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-houtputvar)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to identify the output for the section. Section names in the same input file must be unique.

SURFACE

Set this parameter equal to the name used in the [*SURFACE](ch18abk47.md) option to define the surface.

### **Optional parameters: **

AXES

Set AXES=LOCAL if output is desired in the local coordinate system. Set AXES=GLOBAL (default) to output quantities in the global coordinate system.

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

UPDATE

Set UPDATE=NO if output is desired in the original local system of coordinates. Set UPDATE=YES (default) to output quantities in a local system of coordinates that rotates with the average rigid body motion of the surface section. This parameter is relevant only if AXES=LOCAL and the NLGEOM parameter is active in the step.

### **Optional data lines: **

**First line:**

Leave this line blank to allow Abaqus to define the anchor point.

**Second line:**

Leave this line blank to allow Abaqus to define the axes.

**Third line:**

Omit both the first and second data lines for AXES=GLOBAL or to allow Abaqus to define the anchor point and the axes for AXES=LOCAL. Repeat the third data line as often as necessary: each line defines a table. If this line is omitted, all appropriate variables (["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)) will be output.

**Figure 18.5–1** User-defined local coordinate system.

![](../graphics/oprintfile-localsys-nls.png)




