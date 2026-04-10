# *TRANSPORT VELOCITY







### *TRANSPORT VELOCITYSpecify angular transport velocity.

This option is used to define the angular velocity of material transported through the mesh of a deformable body or the transport of material relative to the reference node of a rigid body during a steady-state transport analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Steady-state transport analysis," Section 6.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["Symmetric model generation," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)
- ["UMOTION," Section 1.1.44 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-umotion)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve (defined in the [*AMPLITUDE](ch01abk09.md) option) that gives the time variation of the velocity throughout the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). 

If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

USER

Include this parameter to indicate that the magnitude of the rotational velocity will be defined in user subroutine [`UMOTION`](../sub/sub-link.md#sub-xsl-umotion). If this parameter is used, any magnitudes defined by the data lines can be redefined in the user subroutine.

### **Data lines to define rotational motion: **

**First line:**

Repeat this data line as often as necessary to define rotational motion on nodes of different parts of the model.




