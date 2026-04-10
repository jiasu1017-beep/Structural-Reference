# *TIE







### *TIEDefine surface-based tie and cyclic symmetry constraints or coupled acoustic-structural interactions.

This option is used to impose tie constraints, cyclic symmetry constraints, or coupled acoustic-structural interactions between pairs of surfaces.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Mesh tie constraints," Section 35.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ptiedconstraint)
- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the constraint.

### **Optional, mutually exclusive parameters: **

POSITION TOLERANCE

Set this parameter equal to a cutoff distance that is used to determine which nodes on the slave surface are tied to the master surface. The calculation of the distance between the slave and master surface for a particular slave node depends on factors such as shell element thickness, the setting of the TYPE parameter, and the types of surfaces involved. Slave nodes that do not satisfy the position tolerance are not tied to the master surface. The default value for this tolerance distance depends on the type of formulation and surfaces used in the constraints.

TIED NSET

Set this parameter equal to the node set label of the node set that includes the nodes on the slave surface that will be tied to the master surface. Nodes not included in this node set will not be tied.

### **Optional parameters: **

ADJUST

Set ADJUST=YES (default) to move all tied nodes on the slave surface onto the master surface in the initial configuration, without any strain.

Set ADJUST=NO if the slave nodes will not be moved. This is the default if the slave surface belongs to a substructure or if one or more of the surfaces is beam element-based.

CONSTRAINT RATIO

This parameter applies only when two surfaces with rotational degrees of freedom are tied with an offset but the NO ROTATION parameter is used.

Set this parameter equal to the fractional distance between the master reference surface and the slave node at which the translational constraint should act. By default, Abaqus will attempt to choose this distance such that the translational constraint acts precisely at the interface.

CYCLIC SYMMETRY

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to invoke a constraint between the faces bounding a repetitive sector of a cyclic symmetric structure. This parameter can be used only in conjunction with the [*CYCLIC SYMMETRY MODEL](ch03abk92.md) option.

NO ROTATION

Include this parameter if rotation degrees of freedom should not be tied. If this parameter is omitted, any existing rotation degrees of freedom will be tied if applicable, in addition to the translation degrees of freedom.

NO THICKNESS

Include this parameter to ignore shell thickness effects in calculations involving position tolerances and adjustments for initial gaps.

TYPE

Set TYPE=SURFACE TO SURFACE (default for most cases in Abaqus/Standard) to have the tie coefficients generated such that stress accuracy is optimized for the specified surface type pairings.

Set TYPE=NODE TO SURFACE (default for all cases in Abaqus/Explicit) to have the tie coefficients generated according to the interpolation functions at the point where the slave node projects onto the master surface.

### **Data lines to define the surfaces forming the constraint pairs: **

**First line:**

Repeat this data line as often as necessary to define all the surfaces forming the constraint pairs. Each data line defines a pair of surfaces that will be tied together.




