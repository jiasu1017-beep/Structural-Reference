# *SUBSTRUCTURE GENERATE







### *SUBSTRUCTURE GENERATESubstructure generation analysis.

This option is used to indicate that the step should be analyzed as a substructure generation step.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **This option is not supported in a model defined in terms of an assembly of part instances.

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### **Required parameter: **

TYPE

Set this parameter equal to the identifier to be assigned to this substructure in a substructure library. The identifier must be *Z* followed by a number that cannot exceed 9999.

Substructure identifiers must be unique within a library. If a substructure already exists in the library with this same identifier, the analysis will terminate with an error message unless the OVERWRITE parameter is specified.

### **Optional parameters: **

ELSET

If element output recovery is needed, including all element nodes in the selective recovery node set generally is insufficient since an element can have Abaqus internal nodes. 

Set this parameter equal to the name of the element set that contains all the elements in the regions of the substructure where you want to recover results. 

GRAVITY LOAD

Set GRAVITY LOAD=YES to calculate the substructure's gravity load vectors. The default is GRAVITY LOAD=NO.

LIBRARY

Set this parameter equal to the name of the substructure library on which the substructure data will be written. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such library names. The default library name is *jobname*.

MASS MATRIX

Set MASS MATRIX=YES to calculate the substructure's reduced mass matrix. The default is MASS MATRIX=NO.

NSET

Set this parameter equal to the name of the node set that contains the nodes of the substructure where you want to recover results. This node set must contain all nodes for which node output can be requested in a substructure usage analysis. 

If the NSET parameter is omitted but the ELSET parameter is used, the recovery matrix corresponding to all the element nodes in the specified element set is generated.  If both the NSET and ELSET parameters are used, the recovery matrix for the union of the node set and the set of all the element nodes for all the elements in the element set is generated. If both the NSET and ELSET parameters are omitted, the recovery matrix for all eliminated nodes is generated (default case). 

OVERWRITE

Include this parameter to overwrite an existing substructure with the same TYPE identifier in the library. The default is no overwrite.

PROPERTY EVALUATION

Set this parameter equal to the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the substructure generation. If this parameter is omitted, Abaqus/Standard will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity in the [*SUBSTRUCTURE GENERATE](ch18abk42.md) step.

RECOVERY MATRIX

Set RECOVERY MATRIX=NO to specify that output of element or nodal information is not available within this substructure. The default is RECOVERY MATRIX=YES, indicating that recovery of eliminated variables is possible for most analysis procedures. 

If RECOVERY MATRIX=NO, the NSET and ELSET parameters are ignored.

STRUCTURAL DAMPING MATRIX

Set STRUCTURAL DAMPING MATRIX=YES to calculate the substructure's reduced structural damping matrix. The default is STRUCTURAL DAMPING MATRIX=NO.

VISCOUS DAMPING MATRIX

Set VISCOUS DAMPING MATRIX=YES to calculate the substructure's reduced viscous damping matrix. The default is VISCOUS DAMPING MATRIX=NO.

**There are no data lines associated with this option.**



