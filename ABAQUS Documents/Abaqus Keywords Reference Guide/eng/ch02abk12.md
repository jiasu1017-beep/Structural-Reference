# *BOUNDARY







### *BOUNDARYSpecify boundary conditions.

This option is used to prescribe boundary conditions at nodes or to specify the driven nodes in a submodeling analysis. In Abaqus/Standard it is also used to define primary and secondary bases for modal superposition procedures and to prescribe boundary conditions at phantom nodes for enriched elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Model,  Step

**Abaqus/CAE: **Load module; fluid cavity pressure and generalized plane strain boundary conditions are not supported.

##### **References:**

- ["Defining a model in Abaqus," Section 1.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-imodel)
- ["Boundary conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundary)
- ["Boundary conditions in Abaqus/CFD," Section 34.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundarycfd)
- ["DISP," Section 1.1.4 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udisp)
- ["VDISP," Section 1.2.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpdisp)
- ["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)
- ["Node-based submodeling," Section 10.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asubmodeldisp)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)
- ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)

### Prescribing boundary conditions at nodes

### **No parameters are used when fixed boundary conditions are specified as model data. **

### **Optional parameters (history data only): **

AMPLITUDE

This parameter is relevant only when some of the variables being prescribed have nonzero magnitudes. Set this parameter equal to the name of the amplitude curve defining the magnitude of the prescribed boundary conditions (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted in an Abaqus/Standard analysis, either the reference magnitude is applied linearly over the step (a RAMP function) or it is applied immediately at the beginning of the step and subsequently held constant (a STEP function). The choice of RAMP or STEP function depends on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). There are two exceptions. The first is when displacement or rotation components are given with TYPE=DISPLACEMENT, for which the default is always a RAMP function. The second is when displacement or rotation components in a static step or in a dynamic step with APPLICATION=QUASI-STATIC are given with TYPE=VELOCITY, for which the default is always a STEP function.

If this parameter is omitted in an Abaqus/Explicit or an Abaqus/CFD analysis, the reference magnitude is applied immediately at the beginning of the step and subsequently held constant (a STEP function). 

In an Abaqus/Standard dynamic or modal dynamic procedure, amplitude curves specified for TYPE=DISPLACEMENT or TYPE=VELOCITY will be smoothed automatically. In an Abaqus/Explicit analysis, the user must request that such amplitude curves are smoothed. For more information, see ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude).

BLOCKING

This parameter applies only to Abaqus/Explicit analyses when the USER parameter is specified.

Set BLOCKING=YES (default) to enable blocking for a given node set. The blocking size will be set to a predefined value in Abaqus/Explicit.

Set BLOCKING=NO to disable blocking.

FIXED

This parameter applies only to Abaqus/Standard analyses and cannot be used with the TYPE and USER parameters.

Include this parameter to indicate that the values of the variables being prescribed with this [*BOUNDARY](ch02abk12.md) option should remain fixed at their current values at the start of the step. If this parameter is used, any magnitudes given on the data lines are ignored. This parameter is ignored if it is used in the first step of an analysis.

LOAD CASE

This parameter applies only to Abaqus/Standard analyses. It is ignored in all procedures except [*BUCKLE](ch02abk16.md).

Set this parameter equal to 1 (default) or 2. LOAD CASE=1 can be used to define boundary conditions for the applied loads, and LOAD CASE=2 can be used to define antisymmetry boundary conditions for the buckling modes.

NAME

This parameter applies only to Abaqus/Explicit analyses when the USER parameter is specified.

Set this parameter equal to the name that will be used to reference the boundary condition in user subroutine [`VDISP`](../sub/sub-link.md#sub-xsl-vdisp). Boundary names that appear in an Abaqus/Explicit analysis must be unique. They cannot begin with a number, and they must adhere to the naming convention for labels. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such names.

OP

Set OP=MOD (default) to modify existing boundary conditions or to add boundary conditions to degrees of freedom that were previously unconstrained.

Set OP=NEW if all boundary conditions that are currently in effect should be removed. To remove only selected boundary conditions, use OP=NEW and respecify all boundary conditions that are to be retained.

If a boundary condition is removed in a stress/displacement analysis in Abaqus/Standard, it will be replaced by a concentrated force equal to the reaction force calculated at the restrained degree of freedom at the end of the previous step. If the step is a general nonlinear analysis step, this concentrated force will then be removed according to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. Therefore, if the default amplitudes are used, the concentrated force will be reduced linearly to zero over the period of the step in a static analysis and immediately in a dynamic analysis.

The OP parameter must be the same for all uses of the [*BOUNDARY](ch02abk12.md) option within a single step except in a [*BUCKLE](ch02abk16.md) step, where OP=NEW can be used with LOAD CASE=2 even when OP=MOD is used with LOAD CASE=1.

PHANTOM

This parameter applies only to enriched elements in Abaqus/Standard.

Set PHANTOM=NODE to apply boundary conditions to a phantom node that is originally located coincident with the specified real node in an enriched element.

Set PHANTOM=EDGE to apply boundary conditions to a phantom node located at an element edge between the two specified real corner nodes in an enriched element. This setting applies only to nodes with pore pressure degrees of freedom.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for boundary conditions applied to nodes on the boundary of an adaptive mesh domain. If boundary conditions are applied to nodes in the interior of an adaptive mesh domain, these nodes will always follow the material. Abaqus/Explicit will create a Lagrangian boundary region automatically for surface-type constraints (symmetry planes, moving boundary planes, and fully clamped boundaries).

Set REGION TYPE=LAGRANGIAN (default) to apply the boundary conditions to a Lagrangian boundary region. The edge of a Lagrangian boundary region will follow the material while allowing adaptive meshing along the edge and in the interior of the region.

Set REGION TYPE=SLIDING to define a sliding boundary region. The edge of a sliding boundary region will slide over the material. Adaptive meshing will occur on the edge and in the interior of the region. Mesh constraints are typically applied on the edge of a sliding boundary region to fix it spatially.

Set REGION TYPE=EULERIAN to apply the boundary conditions to an Eulerian boundary region. This option is used to create a boundary region across which material can flow and is typically used with velocity boundary conditions. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

TYPE

This parameter cannot be used with the FIXED parameter.

This parameter is used in a stress/displacement analysis to specify whether the magnitude is in the form of a displacement history, a velocity history, or an acceleration history. In an Abaqus/Standard analysis TYPE=VELOCITY should normally be used to specify finite rotations.

Set TYPE=DISPLACEMENT (default) to give a displacement history. Abaqus/Explicit does not admit jumps in displacement. If no amplitude is specified, Abaqus/Explicit will ignore the user-supplied displacement value and enforce a zero displacement boundary condition. See ["Boundary conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundary), for details. In Abaqus/CFD this type is used to prescribe mesh displacements.

Set TYPE=VELOCITY to give a velocity history. Velocity histories can be specified in static analyses in Abaqus/Standard, as discussed in “Prescribing large rotations” in ["Boundary conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundary). In this case the default variation is STEP. Velocity histories are not used in Abaqus/CFD.

Set TYPE=ACCELERATION to give an acceleration history. Acceleration histories should not be used in Abaqus/CFD or in static analysis steps in Abaqus/Standard.

If amplitude functions are specified as piecewise linear functions in Abaqus/Explicit and a displacement history is used, there will be a jump in the velocity and a spike in the acceleration at points on the curve where the curve changes slope. This will result in a “noisy” solution. If possible, use [*AMPLITUDE](ch01abk09.md), DEFINITION=SMOOTH STEP; [*AMPLITUDE](ch01abk09.md), SMOOTH; or [*BOUNDARY](ch02abk12.md), TYPE=VELOCITY or TYPE=ACCELERATION. For TYPE=ACCELERATION the value of the initial velocity (given in [*INITIAL CONDITIONS](ch09abk18.md), TYPE=VELOCITY) must be specified to obtain the correct displacement history.

USER

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses and cannot be used with the FIXED parameter.

For Abaqus/Standard include this parameter to indicate that any nonzero magnitudes associated with variables prescribed through this option can be redefined in user subroutine [`DISP`](../sub/sub-link.md#sub-xsl-disp). Any magnitudes defined on the data lines of the option (and possibly modified by the AMPLITUDE parameter) will be passed into user subroutine [`DISP`](../sub/sub-link.md#sub-xsl-disp) and can be redefined in subroutine [`DISP`](../sub/sub-link.md#sub-xsl-disp). The value of the TYPE parameter is ignored when this option is used.

For Abaqus/Explicit include this parameter to indicate that the boundary value associated with variables prescribed through this option are to be defined in user subroutine [`VDISP`](../sub/sub-link.md#sub-xsl-vdisp). Any magnitudes defined on the data lines of the option are ignored and the amplitude, if the AMPLITUDE parameter is included, is passed into the [`VDISP`](../sub/sub-link.md#sub-xsl-vdisp) routine for your usage. The type of user prescribed variable in subroutine [`VDISP`](../sub/sub-link.md#sub-xsl-vdisp) is determined by the TYPE parameter. The NAME parameter can be used in user subroutine [`VDISP`](../sub/sub-link.md#sub-xsl-vdisp) to distinguish multiple boundary conditions. Only translational and rotational degrees of freedom are supported for user-prescribed boundary conditions.

### **Optional, mutually exclusive parameters for matrix generation and direct-solution, steady-state dynamics analysis (history data only): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the boundary condition.

REAL

Include this parameter (default) to define the real (in-phase) part of the part of the boundary condition.

### **Data lines to define zero-valued boundary conditions using the "type" format (model data only): **

**First line:**

Repeat this data line as often as necessary to specify fixed boundary conditions at different nodes and degrees of freedom.

### **Data lines to prescribe boundary conditions using the "direct" format when the PHANTOM parameter is not used: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at different nodes and degrees of freedom.

### **Data lines to prescribe boundary conditions using the "direct" format when PHANTOM=NODE: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at different nodes and degrees of freedom.

### **Data lines to prescribe boundary conditions using the "direct" format when PHANTOM=EDGE: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at different nodes and degrees of freedom.

### Defining primary and secondary bases for modal superposition procedures

### **Optional parameter: **

BASE NAME

This parameter is used to define a secondary base and can be used only in a frequency extraction step (["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)). Set this parameter equal to the name of a secondary base (["Dynamic analysis procedures: overview," Section 6.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamicproc)). In subsequent modal superposition steps this base will be excited as specified by the [*BASE MOTION](ch02abk01.md) option that refers to the same base name. If this parameter is not used in a frequency extraction step, the nodes will be assigned to the primary base.

### **Data lines to define a primary or a secondary base within a [*FREQUENCY](ch06abk35.md) procedure: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at different nodes and degrees of freedom.

### Submodel boundary conditions

### **Required parameters: **

STEP

Set this parameter equal to the step number in the global analysis for which the values of the driven variables will be read during this step of the submodel analysis.

SUBMODEL

Include this parameter to specify that the boundary conditions are the “driven variables” in a submodel analysis. Nodes used in this option must be listed in the [*SUBMODEL](ch18abk38.md) model definition option.

### **Optional parameters: **

INC

This parameter can be used only in a static linear perturbation step (["General and linear perturbation procedures," Section 6.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-alinearnonlinear)). Set this parameter equal to the increment in the selected step of the global analysis at which the solution will be used to specify the values of the driven variables. By default, Abaqus/Standard will use the solution at the last increment of the selected step.

OP

Set OP=MOD (default) for existing [*BOUNDARY](ch02abk12.md) conditions to remain, with this option defining boundary conditions to be added or modified.

Set OP=NEW if all boundary conditions that are currently in effect should be removed. To remove only selected boundary conditions, use OP=NEW and respecify all boundary conditions that are to be retained.

If a boundary condition is removed in a stress/displacement analysis, it will be replaced by a concentrated force equal to the reaction force calculated at the restrained degree of freedom at the end of the previous step. If the step is a general nonlinear analysis step, this concentrated force will then be removed according to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. Therefore, by default the concentrated force will be reduced linearly to zero over the period of the step in a static analysis and immediately in a dynamic analysis.

The OP parameter must be the same for all uses of the [*BOUNDARY](ch02abk12.md) option in a step.

SCALE

Set this parameter equal to the value by which the driven variables read from the global analysis are to be scaled. The default is SCALE=1.0.

TIMESCALE

If the submodel analysis step time is different from the global analysis step time, use the TIMESCALE parameter to adjust the time variable for the driven nodes' amplitude functions. The time variable of each driven node's amplitude function is scaled to match the submodel analysis step time. If this parameter is omitted, the time variable is not scaled.

### **Data lines for shell-to-shell or solid-to-solid submodeling: **

**First line:**

Repeat this data line as often as necessary to specify submodel boundary conditions at different nodes and degrees of freedom.

### **Data lines for shell-to-solid submodeling: **

**First line:**

Repeat this data line as often as necessary to specify submodel boundary conditions at different nodes.

### **Data lines for acoustic-to-structure submodeling: **

**First line:**

Repeat this data line as often as necessary to specify submodel boundary conditions at different nodes.




