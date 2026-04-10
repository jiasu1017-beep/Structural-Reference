# *PRESSURE PENETRATION







### *PRESSURE PENETRATIONSpecify pressure penetration loads with surface-based contact.

This option is used to prescribe pressure penetration loading simulated with surface-based contact. 

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Pressure penetration loading," Section 37.1.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-apressurepenetration)

### **Required parameters: **

MASTER

Set this parameter equal to the name of the master surface of the contact pair used in the pressure penetration analysis.

SLAVE

Set this parameter equal to the name of the slave surface of the contact pair used in the pressure penetration analysis.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the fluid pressure during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or ramped up linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). 

OP

Set OP=MOD (default) for existing pressure penetration loads to remain, with this option modifying existing pressure penetration loads or defining additional pressure penetration loads.

Set OP=NEW if all existing pressure penetration loads applied to the model should be removed. New pressure penetration loads can be defined.

PENETRATION TIME

Set this parameter equal to a time period over which the fluid pressure on newly penetrated contact surface segments is ramped up to the current magnitude. The default penetration time period is chosen to be 0.001 of the current step time. This parameter will be neglected in a linear perturbation analysis, in which case the current fluid pressure will be applied immediately once the pressure penetration criterion is satisfied. 

### **Optional, mutually exclusive parameters for matrix generation and steady-state dynamics analysis (direct or modal): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define the pressure penetration loads: **

**First line:**

Repeat this data line as often as necessary to define fluid penetrations from different locations on the surface, possibly with different fluid pressure magnitudes. Alternatively, the [*PRESSURE PENETRATION](ch16abk27.md) option can be repeated (if, for example, a different amplitude reference is needed). 




