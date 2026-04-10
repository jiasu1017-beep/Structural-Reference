# *FLUID CAVITY







### *FLUID CAVITYDefine a fluid cavity.

This option is used to define a surface-based fluid cavity. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to refer to the fluid cavity. 

REF NODE

Set this parameter equal to either the node number of the fluid cavity reference node or the name of a node set containing the fluid cavity reference node. If the name of a node set is chosen, the node set must contain exactly one node.

### **Required, mutually exclusive parameters: **

BEHAVIOR

Set this parameter equal to the name of the [*FLUID BEHAVIOR](ch06abk16.md) option defining the fluid behavior.

MIXTURE

This parameter applies only to Abaqus/Explicit analyses. 

Set MIXTURE=MASS FRACTION (default) to use the mass fraction if the fluid in the fluid cavity is a mixture of ideal gases.

Set MIXTURE=MOLAR FRACTION to use the molar fraction if the fluid in the fluid cavity is a mixture of ideal gases.

### **Optional parameters: **

ADDED VOLUME

Set this parameter equal to the magnitude of the additional volume for the fluid. The additional volume will be added to the actual volume of the cavity that is calculated.

ADIABATIC

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only when an ideal gas model is used. Include this parameter if adiabatic behavior is assumed for the ideal gas. 

AMBIENT PRESSURE

Set this parameter equal to the magnitude of the ambient pressure. For a pneumatic fluid, the ambient pressure will typically be atmospheric pressure.

AMBIENT TEMPERATURE

This parameter applies only to Abaqus/Explicit analyses and is relevant only when heat energy flow is defined for a pneumatic fluid with adiabatic behavior.

Set this parameter equal to the magnitude of the ambient temperature. The ambient temperature will typically be atmospheric temperature. 

CHECK NORMALS

This parameter is relevant only when the surface is defined to form the boundary of the fluid cavity.

Set CHECK NORMALS=YES (default) to check the consistency of the surface normals.

Set CHECK NORMALS=NO to skip the consistency checking for the surface normals.

MINIMUM VOLUME

This parameter applies only to Abaqus/Explicit analyses.

Use this parameter to define the magnitude of the minimum volume for the fluid cavity. If the volume of the cavity (which is equal to the actual volume plus the added volume) drops below the minimum, the minimum value will be used to evaluate the equation of state model.

Set this parameter equal to a positive value to define the minimum volume directly.

Set MINIMUM VOLUME=INITIAL VOLUME to set the minimum volume equal to the initial volume of the cavity. If the initial volume of the fluid cavity is a negative value, the minimum volume will be set equal to zero.

SURFACE

Set this parameter equal to the name of the surface forming the boundary of the fluid cavity. This parameter is required if the ADDED VOLUME parameter is omitted.

### **Data line if the BEHAVIOR parameter is included: **

**First (and only) line:**

### **Data lines if the MIXTURE parameter is included: **

**First line:**

**Second line:**

Repeat this data line as often as necessary to define the initial gas mixture.




