# *ELEMENT OPERATOR OUTPUT







### *ELEMENT OPERATOR OUTPUTWrite element operator output to a SIM document.

This option is used to write thermal matrices to a SIM document in element-by-element or assembled form. It can be used only in uncoupled heat transfer analyses.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Generating thermal matrices," Section 10.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amtxgenerationgeneral)

### **Optional parameters: **

ASSEMBLE

Include this parameter to write assembled matrices. By default, element matrices are written.

DAMPING

Include this parameter to output the heat capacity matrix.

ELSET

Use this parameter to write matrices for a part of the model. Set this parameter equal to the name of an element set that contains all the elements in the selected part of the model. By default, matrices are generated for all supported elements in the whole model, including internal elements. 

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

LOAD

Include this parameter to output the flux selected by the LOADTYPE parameter.

LOADTYPE

Use this parameter to select the type of load for output.

Set LOADTYPE=EXTERNAL (default) to output external heat flux.

Set LOADTYPE=NET to output net heat flux.

STIFFNESS

Include this parameter to output the thermal conductivity matrix.

**There are no data lines associated with this option.**



