# *MATRIX GENERATE







### *MATRIX GENERATEGenerate global or element matrices.

This option is used to generate matrices representing the stiffness, mass, viscous damping, structural damping, or load vectors in a model.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Generating matrices," Section 10.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)

### **At least one of the following parameters is required: **

STIFFNESS

Include this parameter to generate the stiffness matrix.

MASS

Include this parameter to generate the mass matrix.

VISCOUS DAMPING

Include this parameter to generate the viscous damping matrix.

STRUCTURAL DAMPING

Include this parameter to generate the structural damping matrix.

LOAD

Include this parameter to generate the load matrix.

### **The following parameter is required if the model contains solid continuum infinite elements: **

SOLID INFINITE FORMULATION

Set this parameter equal to STATIC to select the static formulation for solid infinite elements. 

Set this parameter equal to DYNAMIC to select the dynamic formulation for solid infinite elements.

### **Optional parameters: **

ELEMENT BY ELEMENT

Include this parameter to generate local element matrices. By default, global assembled matrices are generated.

ELSET

Use this parameter to generate matrices for a part of a model. Set this parameter equal to the name of an element set  that contains all the elements in the selected part of a model. By default, matrices are generated for the whole model.

FIELD

Set FIELD=ALL (default) to indicate that matrices are generated for the structural and acoustic parts of the model.

Set  FIELD=MECHANICAL  to indicate that matrices are generated only for the structural part of the model.

Set  FIELD=ACOUSTIC  to indicate that matrices are generated only for the acoustic part of the model.

MPC

Set MPC=YES (default) to generate the matrices with applied multipoint constraints. The generated matrices will include entries only for the independent degrees of freedom.

Set MPC=NO to skip applying the multipoint constraints during the matrix generation. The matrices will include entries for  all active degrees of freedom in the model.

PROPERTY EVALUATION

Set this parameter equal to the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the matrix generation. If this parameter is omitted, Abaqus/Standard will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity.

PUBLIC NODES

Use this parameter to specify which nodes will be visible in the matrix usage model. Set this parameter equal to the name of the node set that contains all the nodes that will be presented as user-defined nodes during matrix input; all other nodes are designated as internal nodes and effectively hidden. By default, all user-defined nodes are visible in the matrix usage model.

SOURCE

Set SOURCE=ALL (default) to generate matrices including contributions from the finite elements and from the matrix input.

Set SOURCE=ELEMENTS to generate matrices including only contributions from the finite elements.

Set SOURCE=MATRIX INPUT to generate matrices including only contributions from the matrix input. The ELSET and SOURCE=MATRIX INPUT parameters are mutually exclusive.

**There are no data lines associated with this option.**



