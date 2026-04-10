# *CONTROLS







### *CONTROLSReset solution controls.

**Warning:**This option is not needed in most nonlinear analyses, except for use with the parameter ANALYSIS=DISCONTINUOUS. However, if extreme nonlinearities occur, this option may be needed to obtain a solution. ["Commonly used control parameters," Section 7.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergecontrol), contains a discussion of the types of problems that may occur and the use of the [*CONTROLS](ch03abk75.md) option to overcome these problems. This option can also be used in some cases to obtain a solution in a more efficient manner. Use of the option for this latter purpose is intended for experienced users only.

**Products: **Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Convergence and time integration criteria: overview," Section 7.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergeintro)
- ["Commonly used control parameters," Section 7.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergecontrol)
- ["Convergence criteria for nonlinear problems," Section 7.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergcriteria)
- ["Time integration accuracy in transient problems," Section 7.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aautomaticinc)

### **Required, mutually exclusive parameters: **

ANALYSIS

This parameter applies only to Abaqus/Standard analyses.

Set ANALYSIS=DISCONTINUOUS to set parameters that will usually improve efficiency for severely discontinuous behavior, such as frictional sliding or concrete cracking, by allowing relatively many iterations prior to beginning any checks on the convergence rate. This parameter overrides any values that may be set for the variables ![](../graphics/key_eqn00390.gif) and ![](../graphics/key_eqn00391.gif) on the data lines associated with PARAMETERS=TIME INCREMENTATION. A less efficient solution may result if this parameter is set in problems that do not exhibit severely discontinuous behavior.

PARAMETERS

This parameter applies only to Abaqus/Standard analyses.

Set PARAMETERS=FIELD to set parameters for satisfying a field equation. In this case the FIELD parameter can be used to define the field for which the parameters are being given. If the FIELD parameter is omitted, the parameters are being set for all fields that are active in the problem.

Set PARAMETERS=CONSTRAINTS to set tolerances on constraint equations.

Set PARAMETERS=LINE SEARCH to set line search control parameters.

Set PARAMETERS=TIME INCREMENTATION to set time incrementation control parameters.

RESET

Include this parameter to reset all values to their defaults. The option should have no data lines when this parameter is used.

TYPE

Set TYPE=FSI to set the parameters that will be used in deforming-mesh problems involving moving boundaries or deforming geometries in Abaqus/CFD as well as an Abaqus/CFD to Abaqus/Standard or to Abaqus/Explicit co-simulation. This parameter setting can be used only in Abaqus/CFD analyses.

Set TYPE=DIRECT CYCLIC to set parameters that will be used to control the stabilized state and plastic ratcheting detections and to specify when to impose the periodicity condition for direct cyclic analysis.

Set TYPE=VCCT LINEAR SCALING to set the ![](../graphics/key_eqn00135.gif) parameter that will be used with linear scaling for a VCCT debonding analysis.

### **Optional parameters: **

DISTORTION CONTROL

This parameter applies only to Abaqus/CFD analyses when TYPE=FSI, MESH SMOOTHING=EXPLICIT.

Set DISTORTION CONTROL=OFF (default) to deactivate a constraint that acts to prevent negative element volumes in the CFD meshing movement.

Set DISTORTION CONTROL=ON to activate a constraint that acts to prevent negative element volumes in the CFD meshing movement. The DISTORTION CONTROL parameter cannot prevent elements from being distorted due to temporal instabilities and physically unrealistic deformation.

FIELD

This parameter can be used only with PARAMETERS=FIELD in Abaqus/Standard.

Set FIELD=CONCENTRATION to set parameters for the mass concentration field equilibrium equations.

Set FIELD=DISPLACEMENT to set parameters for the displacement field and warping degree of freedom equilibrium equations.

Set FIELD=ELECTRICAL POTENTIAL to set parameters for the electrical potential field equilibrium equations.

Set FIELD=GLOBAL (default) to define one set of parameters to be used for all active fields.

Set FIELD=HYDROSTATIC FLUID PRESSURE to set parameters for the hydrostatic fluid element volume constraint.

Set FIELD=MATERIAL FLOW to set parameters for the material flow degree of freedom for connector elements.

Set FIELD=PORE FLUID PRESSURE to set parameters for the pore liquid volumetric continuity equations.

Set FIELD=PRESSURE LAGRANGE MULTIPLIER to set parameters for the pressure Lagrange multiplier field equations.

Set FIELD=ROTATION to set parameters for the rotation field equilibrium equations.

Set FIELD=TEMPERATURE to set parameters for the temperature field equilibrium equations.

Set FIELD=VOLUMETRIC LAGRANGE MULTIPLIER to set parameters for the volumetric Lagrange multiplier field equations.

MESH SMOOTHING

This parameter applies only to Abaqus/CFD analyses when TYPE=FSI.

Set MESH SMOOTHING=IMPLICIT (default) to choose the implicit algorithm to control mesh smoothing.

Set MESH SMOOTHING=EXPLICIT to choose the explicit algorithm to control mesh smoothing.

### **Data line for TYPE=FSI, MESH SMOOTHING=IMPLICIT: **

**First (and only) line:**

### **Data line for TYPE=FSI, MESH SMOOTHING=EXPLICIT: **

**First (and only) line:**

### **Data lines for PARAMETERS=FIELD: **

**First line:**

**Second line:**

These items rarely need to be reset from their default values.

### **Data line for PARAMETERS=CONSTRAINTS: **

**First (and only) line:**

These items rarely need to be reset from their default values. The relevance of certain parameters depends on the value of the CONVERT SDI parameter on the [*STEP](ch18abk36.md) option.

### **Data line for PARAMETERS=LINE SEARCH: **

**First (and only) line:**

### **Data lines for PARAMETERS=TIME INCREMENTATION: **

**First line:**

The relevance of certain parameters depends on the value of the CONVERT SDI parameter on the [*STEP](ch18abk36.md) option.

**Second line:**

These items rarely need to be reset from their default values.

**Third line:**

These items rarely need to be reset from their default values.

**Fourth line:**

These items rarely need to be reset from their default values.

### **Data line for TYPE=DIRECT CYCLIC: **

**First (and only) line:**

### **Data line for TYPE=VCCT LINEAR SCALING: **

**First (and only) line:**




