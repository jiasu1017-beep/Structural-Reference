# *MATRIX OUTPUT







### *MATRIX OUTPUTOutput generated matrices in various forms.

This option is used to write generated global matrices to files in assembled or element-by-element form. It can be used only in a matrix generation analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Generating matrices," Section 10.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)
- [*MATRIX GENERATE](ch13abk12.md)

### **At least one of the following parameters is required: **

STIFFNESS

Include this parameter to output the stiffness matrix.

MASS

Include this parameter to output the mass matrix.

VISCOUS DAMPING

Include this parameter to output the viscous damping matrix.

STRUCTURAL DAMPING

Include this parameter to output the structural damping matrix.

LOAD

Include this parameter to output the load matrix.

### **Optional parameter: **

FORMAT

Set FORMAT=MATRIX INPUT (default) to specify that the output use the matrix input text format that is consistent with the format used by the matrix definition technique in Abaqus/Standard.

Set FORMAT=LABELS to specify that the output use the standard labeling format.

Set FORMAT=COORDINATE to specify that the output use the common mathematical coordinate format.

**There are no data lines associated with this option.**



