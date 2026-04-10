# *DSLOAD







### *DSLOADSpecify distributed surface loads.

This option is used to prescribe distributed surface loading.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed)
- ["DLOAD," Section 1.1.5 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udload)
- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["Submodeling: overview," Section 10.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asubmodeloverview)
- ["Surface-based submodeling," Section 10.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asubmodelstress)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### Applying distributed loads

### **Required parameter for cyclic symmetry models in steady-state dynamics analyses: **

CYCLIC MODE

Set this parameter equal to the cyclic symmetry mode number of loads that are applied in the current steady-state dynamics procedure.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the load magnitude during the step.

If this parameter is omitted for uniform load types in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step.

Amplitude references are ignored for nonuniform loads given by user subroutine [`DLOAD`](../sub/sub-link.md#sub-xsl-dload) in an Abaqus/Standard analysis. Amplitude references are passed into user subroutine [`VDLOAD`](../sub/sub-link.md#sub-xsl-vdload) in an Abaqus/Explicit analysis.

Only the load magnitude is changed with time. Quantities such as the fluid surface level in hydrostatic pressure loading are not changed.

CONSTANT RESULTANT

Set CONSTANT RESULTANT=NO (default) if surface traction vectors, edge traction vectors, or edge moments are to be integrated over the surface in the current configuration.

Set CONSTANT RESULTANT=YES if surface traction vectors, edge traction vectors, or edge moments are to be integrated over the surface in the reference configuration.

The CONSTANT RESULTANT parameter is valid only for uniform and nonuniform surface tractions and edge loads (including edge moments); it is ignored for all other load types.

FOLLOWER

Set FOLLOWER=YES (default) if a prescribed traction or shell-edge load is to rotate with the surface or shell edge in a large-displacement analysis (live load).

Set FOLLOWER=NO if a prescribed traction or edge load is to remain fixed in a large-displacement analysis (dead load). 

The FOLLOWER parameter is valid only for traction and edge load labels TRVEC, TRVECNU, EDLD, and EDLDNU. It is ignored for all other load labels. 

OP

Set OP=MOD (default) for existing [*DSLOAD](ch04abk42.md)s to remain, with this option modifying existing distributed loads or defining additional distributed loads.

Set OP=NEW if all existing [*DSLOAD](ch04abk42.md)s applied to the model should be removed. New distributed loads can be defined.

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) used to specify the local coordinates in which components of traction or shell-edge loads are specified.

The ORIENTATION parameter is valid only for traction and edge load labels TRSHR, TRSHRNU,  TRVEC, TRVECNU, EDLD, and EDLDNU. It is ignored for all other load labels.

REF NODE

This parameter applies only to Abaqus/Explicit analyses and is relevant only for viscous and stagnation pressure loads when the velocity at the reference node is used.

Set this parameter equal to either the node number of the reference node or the name of a node set containing the reference node. If the name of a node set is chosen, the node set must contain exactly one node. If this parameter is omitted, the reference velocity is assumed to be zero.

### **Optional, mutually exclusive parameters for matrix generation and steady-state dynamics analysis (direct, modal, or subspace): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define distributed surface pressures: **

**First line:**

Repeat this data line as often as necessary to define distributed loads on different surfaces.

### **Data lines to define hydrostatic pressure (Abaqus/Standard only): **

**First line:**

Repeat this data line as often as necessary to define hydrostatic pressure loading on different surfaces.

### **Data lines to define a general surface traction vector, a surface shear traction vector, or a general shell-edge traction vector: **

**First line:**

 For a two-dimensional or axisymmetric analysis, only the first two components of the traction vector direction need to be specified. For the shear traction load labels TRSHR and TRSHRNU, the loading direction is computed by projecting the specified traction vector direction down upon the surface in the reference configuration. For nonuniform loads in Abaqus/Standard the magnitude and traction vector direction must be defined in user subroutine [`UTRACLOAD`](../sub/sub-link.md#sub-xsl-utracload). If given, the magnitude and vector will be passed into the user subroutine in an Abaqus/Standard analysis.

Repeat this data line as often as necessary to define traction vectors on different surfaces.

### **Data lines to define a surface normal traction vector, a shell-edge traction vector (in the normal, transverse, or tangent direction), or a shell-edge moment: **

**First line:**

Repeat this data line as often as necessary to define traction vectors on different surfaces.

### **Data lines to define stagnation pressure loads (Abaqus/Explicit only): **

**First line:**

Repeat this data line as often as necessary to define stagnation pressure loads on different surfaces.

### Applying submodel boundary conditions (Abaqus/Standard only)

### **Required parameters: **

STEP

Set this parameter equal to the step number in the global analysis for which the values of the driven stresses will be read during this step of the submodel analysis.

SUBMODEL

Include this parameter to specify that the distributed loads are the “driven loads” in a submodel analysis. Surfaces used in this option must be among those listed in the [*SUBMODEL](ch18abk38.md) model definition option.

### **Optional parameters: **

INC

This parameter can be used only in a static linear perturbation step (["General and linear perturbation procedures," Section 6.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-alinearnonlinear)).

 Set this parameter equal to the increment in the selected step of the global analysis at which the solution will be used to specify the values of the driven stresses. By default, Abaqus/Standard uses the solution at the last increment of the selected step.

OP

Set OP=MOD (default) for existing [*DSLOAD](ch04abk42.md)s to remain, with this option modifying existing distributed loads or defining additional distributed loads.

Set OP=NEW if all existing [*DSLOAD](ch04abk42.md)s applied to the model should be removed. New distributed loads can be defined.

### **Data lines to define submodeling loads: **

**First line:**

Repeat this data line as often as necessary to specify submodel distributed loads at different surfaces.




