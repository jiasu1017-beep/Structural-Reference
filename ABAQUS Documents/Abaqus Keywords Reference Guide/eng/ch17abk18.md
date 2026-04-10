# *RIGID BODY







### *RIGID BODYDefine a set of elements as a rigid body and define rigid element properties.

This option is used to bind a set of elements and/or a set of nodes and/or an analytical surface into a rigid body and assign a reference node to the rigid body, which can optionally be declared as an isothermal rigid body for fully coupled thermal-stress analysis. It is also used to specify density, thickness, and offset for rigid elements that are part of a rigid body in an Abaqus/Explicit analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Part module and Interaction module

##### **References:**

- ["Rigid elements," Section 30.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-erigid)
- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)
- ["Rigid body definition," Section 2.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidoverview)

### **Required parameter: **

REF NODE

Set this parameter equal to either the node number of the rigid body reference node or the name of a node set containing the rigid body reference node. If the name of a node set is chosen, the node set must contain exactly one node.

### **At least one of the following parameters is required: **

ANALYTICAL SURFACE

Set this parameter equal to the name of the analytical surface to be assigned to the rigid body. 

ELSET

Set this parameter equal to the name of the element set containing the elements to be assigned to the rigid body. An element cannot appear in more than one rigid body.

PIN NSET

Set this parameter equal to the name of a node set containing pin-type nodes to be assigned to the rigid body. This parameter can be used to add nodes to a rigid body or to redefine node types of nodes on elements included in the rigid body by the ELSET parameter. Pin-type nodes have only their translational degrees of freedom associated with the rigid body. A node cannot appear in more than one rigid body definition.

TIE NSET

Set this parameter equal to the name of a node set containing tie-type nodes to be assigned to the rigid body. This parameter can be used to add nodes to a rigid body or to redefine node types of nodes on elements included in the rigid body by the ELSET parameter. Tie-type nodes have both their translational and rotational degrees of freedom associated with the rigid body. A node cannot appear in more than one rigid body definition.

### **Optional parameters: **

ISOTHERMAL

This parameter is used only for fully coupled thermal-stress analysis.

Set this parameter equal to YES to specify an isothermal rigid body. The default is ISOTHERMAL=NO.

POSITION

Set POSITION=INPUT (default) if the location of the reference node is to be defined by the user.

Set POSITION=CENTER OF MASS if the reference node is to be located at the center of mass of the rigid body.

### **Optional parameters (use only when the element set specified contains rigid elements): **

DENSITY

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the density of all of the rigid elements in the element set.

NODAL THICKNESS

This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to indicate that the thickness of the rigid elements should not be read from the data line but should be interpolated from the thickness specified at the nodes with the [*NODAL THICKNESS](ch14abk08.md) option.

OFFSET

This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to define the distance (as a fraction of the rigid element's thickness) from the element's midsurface to the reference surface containing the element's nodes. Since no element level calculations are performed for rigid elements, a specified offset affects only the handling of contact pairs with rigid surfaces formed by rigid elements.

This parameter accepts positive or negative values or the labels SPOS or SNEG. The positive values of the offset are in the direction of the element normal. When OFFSET=0.5 (or SPOS), the top surface of the rigid element is the reference surface. When OFFSET=0.5 (or SNEG), the bottom surface of the rigid element is the reference surface. The default is OFFSET=0, which indicates that the middle surface of the rigid element is the reference surface.

### **There are no data lines associated with this option in an Abaqus/Standard analysis. **

### **Data line for R2D2 elements in an Abaqus/Explicit analysis: **

**First (and only) line:**

### **Data line for RAX2, R3D3, and R3D4 elements in an Abaqus/Explicit analysis: **

**First (and only) line:**




