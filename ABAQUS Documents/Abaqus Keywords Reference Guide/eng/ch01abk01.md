# *ACOUSTIC FLOW VELOCITY







### *ACOUSTIC FLOW VELOCITYSpecify flow velocities as a predefined field for acoustic elements.

This option is used to specify the fluid flow velocity of node sets or individual nodes for acoustic analysis. This option defines an underlying flow, about which the acoustic analysis is a linear perturbation.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)

### **Required, mutually exclusive parameters: **

ROTATION

Include this parameter to define a flow velocity field due to a rigid body rotation about an axis.

TRANSLATION

Include this parameter to give the *x*-, *y*-, and *z*-components of translational flow velocity in the global coordinate system or in the local coordinate system if [*TRANSFORM](ch19abk11.md) was used at these nodes. Translational flow velocity is the default.

### **Optional parameter: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve (defined in the [*AMPLITUDE](ch01abk09.md) option) that gives the time variation of the flow velocity throughout the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). 

If this parameter is omitted, the default is a STEP function.

### **Data lines to define translational flow velocity (TRANSLATION): **

**First line:**

Repeat this data line as often as necessary to define translational flow velocity for different nodes and degrees of freedom.

### **Data lines to define rotational flow velocity (ROTATION): **

**First line:**

Repeat this data line as often as necessary to define rotational flow velocity for different nodes.




