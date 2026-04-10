# *MATRIX ASSEMBLE







### *MATRIX ASSEMBLEDefine stiffness, mass, or damping matrices for a part of the model.

This option can be used to identify a stiffness, mass, or damping matrix that will be assembled into the corresponding global finite element matrix. This matrix must have been input previously by using the [*MATRIX INPUT](ch13abk13.md) option. The option also unites all the matrices from the same original model and allows you to remap their user nodes to new labels. Matrices from different original models must be specified by repeating the [*MATRIX ASSEMBLE](ch13abk10.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Defining matrices," Section 2.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-idefiningmatrices)
- [*MATRIX INPUT](ch13abk13.md)

### **At least one of the following parameters is required: **

MASS

Set this parameter equal to the name of the mass matrix.

STIFFNESS

Set this parameter equal to the name of the stiffness matrix.

STRUCTURAL DAMPING

Set this parameter equal to the name of the structural damping matrix.

VISCOUS DAMPING

Set this parameter equal to the name of the viscous damping matrix.

### **Optional parameter: **

NSET

Use this parameter to remap nodes of the assembled matrices. Set this parameter equal to the name of the node set that contains the new node labels corresponding to all user-defined nodes of the matrices. The size of the node set and the order of the nodes in the set must fully correspond to the combined set of nodes of all the matrices that are specified in this option. If necessary, use an unsorted node set to obtain the correct mapping. The matrix nodes are assumed to be sorted in ascending order of their original labels that were defined at generation or specified in the matrix data.

If this parameter is omitted, all user-defined nodes retain their original labels.

**There are no data lines associated with this option.**



