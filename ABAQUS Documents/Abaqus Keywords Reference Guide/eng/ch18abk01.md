# *SECTION CONTROLS







### *SECTION CONTROLSSpecify section controls.

**Warning:**Using values larger than the default values for hourglass control can produce excessively stiff response and sometimes can even lead to instability if the values are too large. Hourglassing that occurs with the default hourglass control parameters is usually an indication that the mesh is too coarse. Therefore, it is generally better to refine the mesh than to add stronger hourglass control.

This option is used to
- choose a nondefault hourglass control approach for reduced-integration elements in Abaqus/Standard and Abaqus/Explicit and modified tetrahedral or triangular elements in Abaqus/Standard,
- scale the default coefficients used in the hourglass control, and
- activate distortion control for solid elements.

 In Abaqus/Explicit this option is also used to- select a nondefault kinematic formulation for 8-node brick elements,
- choose the second-order accurate formulation for solids and shells,
- scale the drill stiffness of shell elements,
- turn off the drill stiffness in small-strain shell elements S3RS and S4RS,
- introduce the stresses in membrane elements from the initial configuration gradually into the model,
- scale the linear and quadratic bulk viscosities,
- specify additional control parameters for smoothed particle hydrodynamic analyses,
- specify whether elements must be deleted when they are completely damaged,
- specify a value of the scalar degradation parameter at or above which elements are assumed to be completely damaged, and
- specify control parameters related to smoothed particle hydrodynamic (SPH) analyses.

This option is used in conjunction with the [*MEMBRANE SECTION](ch13abk16.md), [*SHELL GENERAL SECTION](ch18abk14.md), [*SHELL SECTION](ch18abk15.md), and/or [*SOLID SECTION](ch18abk22.md) options. It can be used with [*BEAM SECTION](ch02abk06.md) and [*BEAM GENERAL SECTION](ch02abk05.md) to scale the linear and bulk viscosities. It can also be used with the [*SOLID SECTION](ch18abk22.md), [*SHELL SECTION](ch18abk15.md), [*MEMBRANE SECTION](ch13abk16.md), [*COHESIVE SECTION](ch03abk24.md), and [*CONNECTOR SECTION](ch03abk50.md) options to- specify whether elements must be deleted when they are completely damaged,
- specify a value of the scalar degradation parameter at or above which elements are assumed to be completely damaged, and,
- in Abaqus/Standard, specify the viscosity coefficient that controls the viscous regularization.

For an import analysis the necessary [*SECTION CONTROLS](ch18abk01.md) settings must be selected in the original analysis, even if some are not applicable for the original analysis; the settings specified in the original analysis are passed into the import analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Mesh module

##### **References:**

- ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)
- [*COHESIVE SECTION](ch03abk24.md)
- [*CONNECTOR SECTION](ch03abk50.md)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)
- [*SOLID SECTION](ch18abk22.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the section control definition. All section control names in the same input file must be unique.

### **Optional parameters: **

CONVERSION CRITERION

This parameter applies only to Abaqus/Explicit analyses involving the conversion of continuum elements to SPH particles.

Set CONVERSION CRITERION=TIME (default) to specify the time when continuum elements are to convert to SPH particles.

Set CONVERSION CRITERION=STRAIN to specify the maximum principal strain (absolute value) when continuum elements are to convert to SPH particles.

Set CONVERSION CRITERION=STRESS to specify the maximum principal stress (absolute value) when continuum elements are to convert to SPH particles.

Set CONVERSION CRITERION=USER to specify a used-defined criterion when continuum elements are to convert to SPH particles.

DISTORTION CONTROL

This parameter applies to Abaqus/Explicit analyses and to solid sections in Abaqus/Standard analyses containing C3D10I elements.

Set DISTORTION CONTROL=YES to activate a constraint that acts to prevent negative element volumes or other excessive distortion for crushable materials. This is the default value for elements with hyperelastic or hyperfoam materials. The DISTORTION CONTROL parameter is not relevant for linear kinematics and cannot prevent elements from being distorted due to temporal instabilities, hourglass instabilities, or physically unrealistic deformation.

Set DISTORTION CONTROL=NO to deactivate a constraint that acts to prevent negative element volumes or other excessive distortion for crushable materials. This value is the default except for elements with hyperelastic or hyperfoam materials.

DRILL STIFFNESS

This parameter applies only to the small-strain shell elements S3RS and S4RS.

Set DRILL STIFFNESS=ON (default) to activate the constraint against the drill mode in S3RS and S4RS elements. 

Set DRILL STIFFNESS=OFF to deactivate the constraint against the drill mode. Deactivating the drill constraint can result in large values for the rotation degrees of freedom at the nodes of these elements. 

The drill constraint is always active for finite-strain conventional shell elements such as S4R. 

ELEMENT CONVERSION

This parameter applies only to Abaqus/Explicit analyses involving the conversion of continuum elements to SPH particles.

Set ELEMENT CONVERSION=NO (default) to prevent continuum elements from converting to SPH particles.

Set ELEMENT CONVERSION=YES to allow continuum elements to convert to SPH particles.

ELEMENT DELETION

This parameter applies to all elements with progressive damage behavior, except connector elements in Abaqus/Explicit.

Set ELEMENT DELETION=YES to allow element deletion when the element has completely damaged. This value is the default for all elements with a damage evolution model. However, this value is not applicable to pore pressure cohesive elements.

Set ELEMENT DELETION=NO to allow fully damaged elements to remain in the computations. The element retains a residual stiffness given by the specified value of MAX DEGRADATION. In addition, elements with three-dimensional stress states (including generalized plane strain elements) can sustain hydrostatic compressive stresses, and elements with one-dimensional stress states can sustain compressive stresses. This value is the default for pore pressure cohesive elements and is not available for beam elements.

HOURGLASS

Set HOURGLASS=COMBINED to define the viscous-stiffness form of hourglass control for solid and membrane elements with reduced integration in Abaqus/Explicit.

Set HOURGLASS=ENHANCED (default for elements with hyperelastic and hyperfoam materials in Abaqus/Standard and Abaqus/Explicit; default in Abaqus/Standard and only option in Abaqus/Explicit for modified tetrahedral or triangular elements) to define hourglass control that is based on the assumed enhanced strain method for solid, membrane, finite-strain shell elements with reduced integration  and modified tetrahedral or triangular elements in Abaqus/Standard and Abaqus/Explicit. Any data given on the data line will be ignored for this case.

Set HOURGLASS=RELAX STIFFNESS (default for Abaqus/Explicit, except for elements with hyperelastic and hyperfoam materials) to use the integral viscoelastic form of hourglass control for all elements with reduced integration in Abaqus/Explicit. This value is not supported for Eulerian EC3D8R elements.

Set HOURGLASS=STIFFNESS (default for Abaqus/Standard, except for elements with hyperelastic and hyperfoam materials and modified tetrahedral or triangular elements) to define hourglass control that is strictly elastic for all elements with reduced integration in Abaqus/Standard and Abaqus/Explicit and modified tetrahedral or triangular elements in Abaqus/Standard.

Set HOURGLASS=VISCOUS (default for Eulerian EC3D8R elements) to define the hourglass damping used to control the hourglass modes for solid and membrane elements with reduced integration in Abaqus/Explicit.

INITIAL GAP OPENING

This parameter applies only to Abaqus/Standard analyses using pore pressure cohesive elements.

Set this parameter equal to the value of the initial gap opening used in the tangential flow continuity equation for pore pressure cohesive elements. The default value is 0.002.

KERNEL

This parameter applies only to Abaqus/Explicit analyses involving smoothed particle hydrodynamics (SPH).

Set KERNEL=CUBIC (default) to use a cubic spline interpolator for the SPH formalism.

Set KERNEL=QUADRATIC to use a quadratic interpolator for the SPH formalism.

Set KERNEL=QUINTIC to use a quintic interpolator for the SPH formalism.

KINEMATIC SPLIT

Include this parameter to change the kinematic formulation for 8-node brick elements only.

Set KINEMATIC SPLIT=AVERAGE STRAIN (default in Abaqus/Explicit) to use the uniform strain formulation and the hourglass shape vectors in the hourglass control. This is the only option available for Abaqus/Standard.

Set KINEMATIC SPLIT=CENTROID to use the centroid strain formulation and the hourglass base vectors in the hourglass control in Abaqus/Explicit.

Set KINEMATIC SPLIT=ORTHOGONAL to use the centroid strain formulation and the hourglass shape vectors in the hourglass control in Abaqus/Explicit.

If SECOND ORDER ACCURACY=YES, the KINEMATIC SPLIT parameter will be reset to AVERAGE STRAIN in Abaqus/Explicit.

LENGTH RATIO

This parameter applies only to Abaqus/Explicit analyses and is valid only when the DISTORTION CONTROL parameter is used.

Set this parameter equal to ![](../graphics/key_eqn01039.gif) (![](../graphics/key_eqn01040.gif)) to define the length ratio when using distortion control for crushable materials. The default value is ![](../graphics/key_eqn01041.gif).

MAX DEGRADATION

This parameter applies to all elements with progressive damage behavior, except connector elements in Abaqus/Explicit.

Set this parameter equal to the value of the damage variable at or above which a material point will be assumed to be completely damaged. This parameter also determines the amount of residual stiffness that will be retained by elements for which the ELEMENT DELETION parameter is set to NO. For elements other than cohesive elements, connector elements, and elements with plane stress formulations the default value is 1.0 if the element is deleted from the mesh and 0.99 otherwise. For cohesive elements, connector elements, and elements with plane stress formulations the default value is always 1.0.

PERTURBATION

This parameter applies only to Abaqus/Standard analyses. 

Set this parameter equal to a small perturbation to be applied to the second orientation for the FLEXION-TORSION connectors.

RAMP INITIAL STRESS

This parameter applies to membrane elements in Abaqus/Explicit analyses. 

Set this parameter equal to the name of a total time-based amplitude defined to go from an initial value of zero to a final value of one. When this parameter is specified, the element stiffness is controlled until the amplitude value reaches its final value of one, so that the initial stresses are introduced gradually and not abruptly.

SECOND ORDER ACCURACY

This parameter applies only to Abaqus/Explicit analyses; the element formulation is always second-order accurate in Abaqus/Standard.

Set SECOND ORDER ACCURACY=YES to use a second-order accurate formulation for solid or shell elements suitable for problems undergoing a large number of revolutions (> 5). 

Set SECOND ORDER ACCURACY=NO (default) to use the first-order accurate solid or shell elements.

The SECOND ORDER ACCURACY parameter is not relevant for linear kinematics.

VISCOSITY

This parameter applies to cohesive elements, connector elements, and elements with plane stress formulations (plane stress, shell, continuum shell, and membrane elements) in Abaqus/Standard analyses.

Set this parameter equal to the value of the viscosity coefficient used in the viscous regularization scheme for cohesive elements or connector elements or equal to the value of the damping coefficient used in connector failure modeling.  When this parameter is used to specify the viscosity coefficients for the damage model for fiber-reinforced materials, the specified value is applied to all the damage modes. The default value is 0.0.

WEIGHT FACTOR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to ![](../graphics/key_eqn01042.gif) (![](../graphics/key_eqn01043.gif)) to scale the contributions from the constant hourglass stiffness term and the hourglass damping term to the hourglass control formulation. Setting ![](../graphics/key_eqn00549.gif) or ![](../graphics/key_eqn01044.gif) corresponds to pure constant stiffness hourglass control and pure damping hourglass control, respectively. The default is ![](../graphics/key_eqn01045.gif). This option is used only for solid and membrane elements when the HOURGLASS parameter is set equal to COMBINED.

### **Data lines to define the hourglass control, bulk viscosity, drill stiffness, and smoothed particle hydrodynamics-related controls: **

**First line:**

**Second line (optional, to be used only in conjunction with smoothed particle hydrodynamics):**

**Third line (optional, to be used only in conjunction with smoothed particle hydrodynamics to control the size of the particle tracking box):**

**Fourth line (optional, to be used only in conjunction with the conversion of continuum elements to smoothed particle hydrodynamic particles):**




