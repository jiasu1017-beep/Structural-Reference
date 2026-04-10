# *FREQUENCY







### *FREQUENCYExtract natural frequencies and modal vectors.

This option is used to perform eigenvalue extraction to calculate the natural frequencies and corresponding mode shapes of a system.

**Products: **Abaqus/Standard  Abaqus/CAE  Abaqus/AMS  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)

### **Optional parameters: **

ACOUSTIC COUPLING

For the AMS eigensolver and Lanczos eigensolver, set ACOUSTIC COUPLING=ON to include the effect of acoustic-structural coupling during the natural frequency extraction procedure in models with acoustic and structural elements coupled using the [*TIE](ch19abk06.md) option or in models with ASI-type elements. This is the default option for the Lanczos eigensolver.

For the AMS eigensolver and Lanczos eigensolver based on the SIM architecture, set ACOUSTIC COUPLING=PROJECTION to extract the uncoupled acoustic and structural modes and project the acoustic-structural coupling operator during the natural frequency extraction procedure in models with acoustic and structural elements coupled using the [*TIE](ch19abk06.md) option. This is the default option for the AMS eigensolver.

Set ACOUSTIC COUPLING=OFF to omit the projection of the acoustic-structural coupling operator and to ignore the effect of acoustic-structural coupling during natural frequency extraction in models with acoustic and structural elements coupled using the [*TIE](ch19abk06.md) option or in models with ASI-type elements.

This parameter is not relevant for the subspace iteration eigensolver.

DAMPING PROJECTION

This parameter is relevant only for the AMS eigensolver or for the Lanczos eigensolver used in conjunction with the SIM parameter.

Set DAMPING PROJECTION=ON (default) to project the viscous and structural damping operators during the natural frequency extraction procedure. If there is no damping defined in the model, the projection is not performed.

Set DAMPING PROJECTION=OFF to omit the projection of damping operators.

EIGENSOLVER

Set EIGENSOLVER=LANCZOS (default) to invoke the Lanczos eigensolver.

Set EIGENSOLVER=AMS to invoke the automatic multi-level substructuring (AMS) eigensolver.

Set EIGENSOLVER=SUBSPACE to invoke the subspace iteration eigensolver.

NORMALIZATION

Set NORMALIZATION=DISPLACEMENT to normalize the eigenvectors so that the largest displacement, rotation, or acoustic pressure (in coupled acoustic-structural extractions) entry in each vector is unity. Displacement normalization is the default for both the subspace iteration eignensolver and for the Lanczos eigensolver when they are used without the SIM parameter.

Set NORMALIZATION=MASS to normalize the eigenvectors with respect to the structure's mass matrix (the eigenvectors are scaled so that the generalized mass for each vector is unity). Mass normalization is the default and only available option for the AMS eigensolver. Mass normalization is switched on for both the Lanczos eigensolver and the subspace iteration eigensolver when they are used in conjunction with the SIM parameter.

PROPERTY EVALUATION

Set this parameter equal to the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the eigenvalue extraction. If this parameter is omitted, Abaqus/Standard will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency domain viscoelasticity in the [*FREQUENCY](ch06abk35.md) step.

RESIDUAL MODES

This parameter is relevant only for the Lanczos and AMS eigensolvers.

Include this parameter to indicate that residual modes are to be computed. 

SIM

This parameter is relevant only for the Lanczos and subspace iteration eigensolvers.

Include this parameter to indicate that subsequent mode-based linear dynamic analysis steps should use the high-performance versions based on the SIM software architecture. The SIM parameter is turned on by default if the AMS eigensolver is activated. 

### **Optional parameter when EIGENSOLVER=AMS: **

NSET

Set this parameter equal to the name of the node set or include the parameter with no value to allow Abaqus/Standard to automatically select the nodes at which eigenvectors will be computed. If this parameter is omitted, eigenvectors will be computed at all nodes.

### **Data line for a natural frequency extraction when EIGENSOLVER=LANCZOS: **

**First (and only) line:**

### **Data lines for a natural frequency extraction when EIGENSOLVER=AMS: **

**First line:**

**No additional data lines are needed if default residual modes are sufficient or residual modes are not requested. Otherwise, subsequent lines:**

Repeat this line as often as necessary to request residual modes.

### **Data line for a natural frequency extraction when EIGENSOLVER=SUBSPACE: **

**First (and only) line:**




