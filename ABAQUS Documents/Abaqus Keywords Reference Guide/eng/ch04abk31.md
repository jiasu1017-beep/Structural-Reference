# *DLOAD







### *DLOADSpecify distributed loads.

This option is used to prescribe distributed loading. It is also used to apply concentrated or distributed wind, wave, or buoyancy loading in an Abaqus/Aqua analysis or to apply general body, buoyancy, or porous drag force loading in Abaqus/CFD.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  Abaqus/Aqua  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed)
- ["DLOAD," Section 1.1.5 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udload)
- ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)
- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua)

### Applying distributed loads

### **Required parameter for cyclic symmetry models in steady-state dynamics analyses: **

CYCLIC MODE

Set this parameter equal to the cyclic symmetry mode number of loads that are applied in the current steady-state dynamics procedure.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the load magnitude during the step.

If this parameter is omitted for uniform load types in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit or an Abaqus/CFD analysis, the reference magnitude is applied immediately at the beginning of the step.

Amplitude references are ignored for nonuniform loads given by user subroutine [`DLOAD`](../sub/sub-link.md#sub-xsl-dload) in an Abaqus/Standard analysis. Amplitude references are passed into user subroutine [`VDLOAD`](../sub/sub-link.md#sub-xsl-vdload) in an Abaqus/Explicit analysis.

Only the load magnitude is changed with time. Quantities such as the direction of an applied gravity load and the fluid surface level in hydrostatic pressure loading are not changed.

CONSTANT RESULTANT

Set CONSTANT RESULTANT=NO (default) if surface traction vectors, edge traction vectors, or edge moments are to be integrated over the surface in the current configuration.

 Set CONSTANT RESULTANT=YES if surface traction vectors, edge traction vectors, or edge moments are to be integrated over the surface in the reference configuration.  

The CONSTANT RESULTANT parameter is valid only for uniform and nonuniform surface tractions and edge loads (including edge moments); it is ignored for all other load types.

FOLLOWER

Set FOLLOWER=YES (default) if a prescribed traction or shell-edge load is to rotate with the surface or shell edge in a large-displacement analysis (live load).

Set FOLLOWER=NO if a prescribed traction or edge load is to remain fixed in a large-displacement analysis (dead load). 

The FOLLOWER parameter is valid only for traction and edge load labels TRVEC*n*, TRVEC, TRVEC*n*NU, TRVECNU, EDLD*n*, and EDLD*n*NU. It is ignored for all other load labels. 

OP

Set OP=MOD (default) for existing [*DLOAD](ch04abk31.md)s to remain, with this option modifying existing distributed loads or defining additional distributed loads.

Set OP=NEW if all existing [*DLOAD](ch04abk31.md)s applied to the model should be removed. New distributed loads can be defined.

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) used to specify the local coordinates in which components of traction or shell-edge loads are specified.

The ORIENTATION parameter is valid only for traction and edge load labels TRSHR*n*, TRSHR, TRSHR*n*NU, TRSHRNU, TRVEC*n*, TRVEC, TRVEC*n*NU, TRVECNU, EDLD*n*, and EDLD*n*NU. It is ignored for all other load labels.

REF NODE

This parameter applies only to Abaqus/Explicit analyses and is relevant only for viscous and stagnation body force and pressure loads when the velocity at the reference node is used.

Set this parameter equal to either the node number of the reference node or the name of a node set containing the reference node. If the name of a node set is chosen, the node set must contain exactly one node. If this parameter is omitted, the reference velocity is assumed to be zero.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for pressure loads applied to the boundary of an adaptive mesh domain. If a distributed pressure load is applied to a surface in the interior of an adaptive mesh domain, the nodes on the surface will move with the material in all directions (they will be nonadaptive). Abaqus/Explicit will create a boundary region automatically on the surface subjected to the defined pressure load.

Set REGION TYPE=LAGRANGIAN (default) to apply the pressure to a Lagrangian boundary region. The edge of a Lagrangian boundary region will follow the material while allowing adaptive meshing along the edge and within the interior of the region.

Set REGION TYPE=SLIDING to apply the pressure load to a sliding boundary region. The edge of a sliding boundary region will slide over the material. Adaptive meshing will occur along the edge and in the interior of the region. Mesh constraints are typically applied on the edge of a sliding boundary region to fix it spatially.

Set REGION TYPE=EULERIAN to apply the pressure to an Eulerian boundary region. This option is used to create a boundary region across which material can flow. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

### **Optional, mutually exclusive parameters for matrix generation and steady-state dynamics analyses (direct, modal, or subspace): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define all distributed loads except those special cases described below: **

**First line:**

Repeat this data line as often as necessary to define distributed loads for different elements or element sets.

### **Data lines to define a general surface traction vector, a surface shear traction vector, or a general shell-edge traction vector: **

**First line:**

  For a two-dimensional or axisymmetric analysis, only the first two components of the traction vector direction need to be specified. For the shear traction load labels TRSHR*n*, TRSHR, TRSHR*n*NU, or TRSHRNU, the loading direction is computed by projecting the specified traction vector direction down upon the surface in the reference configuration. For nonuniform loads in Abaqus/Standard the magnitude and traction vector direction must be defined in user subroutine [`UTRACLOAD`](../sub/sub-link.md#sub-xsl-utracload). If given, the magnitude and vector will be passed into the user subroutine in an Abaqus/Standard analysis.

Repeat this data line as often as necessary to define traction vectors for different elements or element sets.

### **Data lines to define a surface normal traction vector, a shell-edge traction vector (in the normal, transverse, or tangent direction), or a shell-edge moment: **

**First line:**

Repeat this data line as often as necessary to define traction vectors for different elements or element sets.

### **Data lines to define centrifugal loads and Coriolis forces (Abaqus/Standard only): **

**First line:**

For axisymmetric elements the axis of rotation must be the global *y*-axis, which must be specified as 0.0, 0.0, 0.0, 0.0, 1.0, 0.0.

Repeat this data line as often as necessary to define centrifugal or Coriolis forces for different elements or element sets.

### **Data lines to define rotary acceleration loads (Abaqus/Standard only): **

**First line:**

For two-dimensional elements the axis of rotation direction must be the global *z*-axis (out of the plane of the model), which must be specified as 0.0, 0.0, 1.0.

Repeat this data line as often as necessary to define rotary acceleration loading for different elements or element sets.

### **Data lines to define rotordynamic loads (Abaqus/Standard only): **

**First line:**

Rotordynamic loads are supported only for three-dimensional continuum and cylindrical elements, shell elements, membrane elements, beam elements, and rotary inertia elements. The spinning axis defined as part of the load must be the axis of symmetry for the structure. Therefore, beam elements must be aligned with the symmetry axis. In addition, one of the principal directions of each loaded rotary inertia element must be aligned with the symmetry axis, and the inertia components of the rotary inertia elements must be symmetric about this axis.

Repeat this data line as often as necessary to define rotordynamic loads for different elements or element sets.

### **Data lines to define gravity loading: **

**First line:**

For axisymmetric elements the gravity load must be in the *z*-direction; therefore, only component 2 should be nonzero. For Abaqus/CFD gravity loading defines the gravity vector used with a Boussinesq-type body force in buoyancy driven flow (see ["Specifying gravity loading" in "Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed-gravity)).

Repeat this data line as often as necessary to define gravity loading for different elements or element sets.

### **Data lines to define porous drag load (Abaqus/CFD only): **

**First line:**

Repeat this data line as often as necessary to define porous drag body force loads for different elements or element sets.

### **Data lines to define external and internal pressure in pipe or elbow elements: **

**First line:**

Repeat this data line as often as necessary to define internal or external pressure loading for different pipe or elbow elements or element sets.

### **Data lines to define hydrostatic pressure (Abaqus/Standard only): **

**First line:**

Repeat this data line as often as necessary to define hydrostatic pressure loading for different elements or element sets.

### **Data lines to define external and internal hydrostatic pressure in pipe or elbow elements: **

**First line:**

Repeat this data line as often as necessary to define internal or external pressure loading for different pipe or elbow elements or element sets.

### **Data lines to define viscous body force, stagnation pressure, or stagnation body loads (Abaqus/Explicit only): **

**First line:**

Repeat this data line as often as necessary to define viscous body force, stagnation pressure, or stagnation body loads for different elements or element sets.

### Loads used by Abaqus/Aqua

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the load magnitude during the step. If this parameter is omitted for uniform load types, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). Amplitude references are ignored for nonuniform loads given by user subroutine [`DLOAD`](../sub/sub-link.md#sub-xsl-dload).

Only the load magnitude is changed with time. Quantities such as the fluid surface level in hydrostatic pressure loading are not changed.

OP

Set OP=MOD (default) for existing [*DLOAD](ch04abk31.md)s to remain, with this option modifying existing loads or defining additional loads.

Set OP=NEW if all existing [*DLOAD](ch04abk31.md)s applied to the model should be removed. New distributed loads can be defined.

### **Data lines to define distributed buoyancy forces: **

**First line:**

Repeat this data line as often as necessary to define buoyancy loading for various elements or element sets.

### **Data lines to define distributed transverse fluid or wind drag: **

**First line:**

Repeat this data line as often as necessary to define distributed transverse fluid or wind drag on various elements or element sets.

### **Data lines to define distributed tangential fluid drag: **

**First line:**

Repeat this data line as often as necessary to define distributed tangential fluid drag on various elements or element sets.

### **Data lines to define distributed fluid inertia loading: **

**First line:**

Repeat this data line as often as necessary to define fluid inertia loading for various elements or element sets.

### **Data lines to define concentrated fluid and wind drag loading on the ends of elements: **

**First line:**

Repeat this data line as often as necessary to define concentrated fluid or wind drag loading on the ends of elements.

### **Data lines to define concentrated fluid inertia loading on the ends of elements: **

**First line:**

Repeat this data line as often as necessary to define concentrated fluid inertia loading on the ends of elements.




