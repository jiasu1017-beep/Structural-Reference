# *CLOAD







### *CLOADSpecify concentrated forces and moments.

This option is used to apply concentrated forces and moments at any node in the model. The [*CLOAD](ch03abk22.md) option can also be used to specify a fluid reference pressure for incompressible flow in an Abaqus/CFD analysis and to specify concentrated buoyancy, drag, and inertia loads in an Abaqus/Aqua analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  Abaqus/Aqua  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Concentrated loads," Section 34.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploadgeneral)
- ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua)
- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)

### Applying concentrated loads

### **Required parameter for reading concentrated nodal force from an output database file: **

FILE

Set this parameter equal to the name of the output database file from which the data are to be read. The file extension is optional.

### **Required parameter for cyclic symmetry models in steady-state dynamics analyses: **

CYCLIC MODE

Set this parameter equal to the cyclic symmetry mode number of loads that are applied in the current steady-state dynamics procedure.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the load during the step.

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step.

FOLLOWER

Include this parameter if the direction of the load is assumed to rotate with the rotation at this node.

This parameter should be used only for large-displacement analysis and can be used only at nodes with active rotational degrees of freedom (such as the nodes of beam or shell elements).

Concentrated buoyancy, drag, and fluid inertia loads in Abaqus/Aqua analyses are automatically considered to be follower forces, so this parameter is not necessary in those cases. 

In general, UNSYMM=YES should be used on the [*STEP](ch18abk36.md) option in conjunction with the FOLLOWER parameter in [*DYNAMIC](ch04abk43.md) and [*STATIC](ch18abk31.md) analyses in Abaqus/Standard. The UNSYMM parameter is ignored in eigenvalue analyses (such as [*BUCKLE](ch02abk16.md) or [*FREQUENCY](ch06abk35.md)) since Abaqus/Standard can perform an eigenvalue extraction only on symmetric matrices.

INC

This parameter is relevant only when the FILE  parameter is used. 

Set this parameter equal to the increment in the selected step of the previous analysis from which the concentrated nodal forces will be read. By default, the concentrated nodal forces will be read from the last increment of the step specified on the STEP parameter or from the last step if the STEP parameter is omitted.

LOAD CASE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the load case number. This parameter is used in [*RANDOM RESPONSE](ch17abk07.md) analysis (["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)), when it is the cross-reference for the load case on the [*CORRELATION](ch03abk77.md) option. The parameter's value is ignored in all other procedures.

OP

Set OP=MOD (default) for existing [*CLOAD](ch03abk22.md)s to remain, with this option modifying existing concentrated loads or defining additional concentrated loads.

Set OP=NEW if all existing [*CLOAD](ch03abk22.md)s applied to the model should be removed. New concentrated loads can be defined.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for concentrated loads applied on the boundary of an adaptive mesh domain. If concentrated loads are applied to nodes in the interior of an adaptive mesh domain, these nodes will always follow the material.

Set REGION TYPE=LAGRANGIAN (default) to apply a concentrated load to a node that follows the material (nonadaptive).

Set REGION TYPE=SLIDING to apply a concentrated load to a node that can slide over the material. Mesh constraints are typically applied to the node to fix it spatially.

Set REGION TYPE=EULERIAN to apply a concentrated load to a node that can move independently of the material. This option is used only for boundary regions where the material can flow into or out of the adaptive mesh domain. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

STEP

This parameter is relevant only when the FILE parameter is used. 

Set this parameter equal to the step number of the previous analysis from which the concentrated nodal forces will be read. By default, the concentrated nodal forces will be read from the last step of the previous analysis.

### **Optional, mutually exclusive parameters for matrix generation and steady-state dynamics analysis: **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define concentrated loads for specific degrees of freedom: **

**First line:**

Repeat this data line as often as necessary to define concentrated loads.

### Applying a fluid reference pressure in Abaqus/CFD

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the fluid reference pressure during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*CLOAD](ch03abk22.md)s to remain, with this option modifying existing fluid reference pressures.

Set OP=NEW if all existing [*CLOAD](ch03abk22.md)s applied to the model should be removed.

### **Data lines to define a fluid reference pressure for incompressible flow in Abaqus/CFD: **

**First line:**

Repeat this data line as often as necessary to define reference pressures; however, only the last specified hydrostatic pressure load in a given fluid domain is applied.

### Applying Abaqus/Aqua loads

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the load during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*CLOAD](ch03abk22.md)s to remain, with this option modifying existing concentrated loads or defining additional concentrated loads.

Set OP=NEW if all existing [*CLOAD](ch03abk22.md)s applied to the model should be removed.

### **Data lines to define concentrated buoyancy forces: **

**First line:**

Repeat this data line as often as necessary to define concentrated buoyancy at various nodes or node sets.

### **Data lines to define concentrated fluid drag loading: **

**First line:**

**Second line:**

Give the following direction cosines in the local coordinate system if the [*TRANSFORM](ch19abk11.md) option was used at this node:

Repeat this pair of data lines as often as necessary to define concentrated fluid or wind drag loading at various nodes or node sets.

### **Data lines to define concentrated fluid inertia loading: **

**First line:**

**Second line:**

Give the following direction cosines in the local coordinate system if the [*TRANSFORM](ch19abk11.md) option was used at this node:

Repeat this pair of data lines as often as necessary to define concentrated fluid inertia loading for various nodes or node sets.




