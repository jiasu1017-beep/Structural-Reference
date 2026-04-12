# 4.5 Matrix quality check







**Product: **Abaqus/Standard  

**Benefits: **You can now check the quality of the generated stiffness and mass matrices in matrix generation or substructure generation analyses.

**Description: **You can request “rigid body mode” checks for the generated stiffness and mass matrices in the matrix generation or substructure generation procedures. The quality of the generated global assembled matrices is checked in the matrix generation procedure. The quality of the generated condensed substructure matrices is checked in the substructure generation procedure. The matrix check generates six “artificial” rigid body modes and projects the matrices onto the rigid body modal subspace. It is expected that the projected 6 ![](../graphics/rnb_eqn00002.gif) 6 stiffness matrix (also known as the rigid body energy matrix) is close to zero in the absence of the boundary conditions and constraints. To perform the stiffness matrix quality check, the boundary conditions and multipoint constraints can be suppressed in the matrix generation procedure. The total inertia statistics for the model are extracted from the projected 6 ![](../graphics/rnb_eqn00002.gif) 6 rigid body mass matrix. You can specify the center of rotation for creating the artificial rotational rigid body modes and calculating the global inertia tensor. If the matrix quality check is requested, the check results are printed in the data (`.dat`) file. 
**References: **

**Abaqus Analysis User's Guide**
- ["Defining substructures," Section 10.1.2](../usb/usb-link.md#usb-anl-asuperelementdef)
- ["Generating matrices," Section 10.3.1](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)

**Abaqus Keywords Reference Guide**
- [*MATRIX CHECK](../key/key-link.md#usb-kws-hmatrixcheck)
- [*MATRIX GENERATE](../key/key-link.md#usb-kws-hmatrixgenerate)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)




