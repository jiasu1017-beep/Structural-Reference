# *MOTION







### *MOTIONSpecify motions as a predefined field.

This option is used to specify motions of node sets or individual nodes during cavity radiation heat transfer analysis, to define the motion of a reference frame in steady-state transport analysis, or to define the velocity of the material transported through the mesh during a static analysis. It can also be used to specify the velocity of an element set representing a conductor transported through the mesh in an eddy current analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- ["Steady-state transport analysis," Section 6.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["Static stress analysis," Section 6.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-astatic)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["UMOTION," Section 1.1.44 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-umotion)

### Specifying motion during cavity radiation heat transfer analysis, steady-state transport analysis, or static analysis

### **Optional, mutually exclusive parameters: **

ROTATION

Include this parameter to define a rigid body rotation about an axis.

TRANSLATION

Include this parameter to give the *x*-, *y*-, and *z*-components of translation in the global coordinate system or in the local coordinate system if [*TRANSFORM](ch19abk11.md) was used at these nodes. Translational motion is the default.

USER

Include this parameter to indicate that magnitudes of motion will be defined in user subroutine [`UMOTION`](../sub/sub-link.md#sub-xsl-umotion). If this parameter is used, any magnitudes defined by the data lines can be redefined in the user subroutine. The value of the TYPE parameter is not relevant when this parameter is used. This parameter cannot be used for steady-state transport analysis.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve (defined in the [*AMPLITUDE](ch01abk09.md) option) that gives the time variation of the motion throughout the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). 

If this parameter is omitted and the translational or rotational motion is given with TYPE=DISPLACEMENT, the default is a RAMP function. If the translational or rotational motion is given with TYPE=VELOCITY, the default is a STEP function for cavity radiation analysis and a RAMP function for steady-state transport analysis.

TYPE

This parameter is used to specify whether the magnitude is in the form of a displacement or a velocity.

Set TYPE=DISPLACEMENT (default for cavity radiation analysis) to give translational or rotational displacement values.

Set TYPE=VELOCITY (only type available for steady-state transport and static analysis) to give translational or rotational velocities. Velocity histories for cavity radiation problems can be specified as illustrated in the discussion on prescribing large rotations in ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation).

### **Data lines to define translational motion (TRANSLATION): **

**First line:**

Repeat this data line as often as necessary to define translational motion for different nodes and degrees of freedom.

### **Data lines to define rotational motion (ROTATION): **

**First line:**

Repeat this data line as often as necessary to define rotational motion for different nodes.

### **Data lines to define motion in user subroutine [`UMOTION`](../sub/sub-link.md#sub-xsl-umotion) (USER): **

**First line:**

Repeat this data line as often as necessary to define the nodes and degrees of freedom that will have their motion prescribed by user subroutine [`UMOTION`](../sub/sub-link.md#sub-xsl-umotion).

### Specifying motion during an eddy current analysis

### **Required parameter: **

ELEMENT

Include this parameter to specify the motion of an element set.

### **Optional, mutually exclusive parameters: **

ROTATION

Include this parameter to define a rigid body rotation about an axis.

TRANSLATION

Include this parameter to give the *x*-, *y*-, and *z*-components of translation in the global coordinate system or in the local coordinate system if [*TRANSFORM](ch19abk11.md) was used at these nodes. Translational motion is the default.

### **Optional parameter: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve (defined in the [*AMPLITUDE](ch01abk09.md) option) that gives the time variation of the motion throughout the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). 

If this parameter is omitted, the default is a STEP function.

### **Data lines to define translational velocity of motion (TRANSLATION): **

**First (and only) line:**

### **Data line to define rotational velocity of motion (ROTATION): **

**First (and only) line:**




