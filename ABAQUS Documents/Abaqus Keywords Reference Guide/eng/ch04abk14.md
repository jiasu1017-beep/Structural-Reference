# *DEPVAR







### *DEPVARSpecify solution-dependent state variables.

This option is used to allocate space at each integration point for solution-dependent state variables. If the [*DEPVAR](ch04abk14.md) option is used, it must appear within the [*MATERIAL](ch13abk08.md) definition for which solution-dependent state variables are needed.

In addition, an output key and a description can be given for some or all of the solution-dependent state variables allocated by this option. If field or history output of solution-dependent state variables is requested using the [*ELEMENT OUTPUT](ch05abk10.md) option, the output identifier for solution-dependent state variables for which a key has been specified under this option will consist of the string “SDV_,” followed by the specified key. Similarly, the descriptions specified under this option will be used in the corresponding field descriptions written to the output database.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["User subroutines: overview," Section 18.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asubroutineover)
- ["User-defined mechanical material behavior," Section 26.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cusermat)
- ["Finite element conversion to SPH particles," Section 15.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asphconversion)

### **Optional, mutually exclusive parameters: **

CONVERT

This parameter applies only to Abaqus/Explicit analyses when continuum finite elements are allowed to convert to SPH particles.

Set this parameter equal to the state variable number controlling the element conversion flag (see ["Finite element conversion to SPH particles," Section 15.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asphconversion)).

DELETE

Set this parameter equal to the state variable number controlling the element deletion flag (see ["User-defined mechanical material behavior," Section 26.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cusermat)).

### **Data line to specify the number of solution-dependent state variables: **

**First line:**

### **Optional data lines to specify output descriptions for select solution-dependent state variables: **

**Second line:**

Repeat this data line for each solution-dependent state variable for which an output key and a description are being defined. If an output key and a description are not given for a solution-dependent state variable, the default output identifier SDV*n* and description “Solution-dependent state variables” will be used.




