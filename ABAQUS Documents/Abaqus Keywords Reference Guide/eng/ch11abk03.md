# *KINEMATIC COUPLING







### *KINEMATIC COUPLINGConstrain all or specific degrees of freedom of a set of nodes to the rigid body motion of a reference node.

This option is used to impose constraints between degrees of freedom of a node or node set and the rigid body motion defined by a reference node. The preferred method of providing a kinematic constraint of this type is the [*COUPLING](ch03abk83.md) option used in conjunction with the [*KINEMATIC](ch11abk02.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Unsupported; this option has been superseded by coupling constraints used in conjunction with the kinematic option.

##### **Reference:**

- ["Kinematic constraints: overview," Section 35.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pkinematic)

### **Required parameter: **

REF NODE

Set this parameter equal to either the node number of the reference node or the name of a node set containing the reference node. If the name of a node set is chosen, the node set must contain exactly one node.

### **Optional parameter: **

ORIENTATION

Set this parameter equal to the name given to the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that specifies the initial orientation of the local system in which the constrained degrees of freedom are defined.

### **Data lines to specify the nodes and degrees of freedom to be constrained: **

**First line:**

Repeat this data line as often as necessary to specify constraints at different nodes and degrees of freedom. When the ORIENTATION parameter is specified, the degrees of freedom are in the referenced local system in the initial configuration; otherwise, they are in the global system. In either case these directions will rotate with the reference node in large-displacement analyses (when the NLGEOM parameter is included on the [*STEP](ch18abk36.md) option).




