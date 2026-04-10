# *COUPLING







### *COUPLINGDefine a surface-based coupling constraint.

This option is used to impose a kinematic or distributing coupling constraint between a reference node and a group of nodes located on a surface. It must be used in conjunction with the [*KINEMATIC](ch11abk02.md) or the [*DISTRIBUTING](ch04abk27.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Coupling constraints," Section 35.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pcoupling)
- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)

### **Required parameters: **

CONSTRAINT NAME

Set this parameter equal to a label that will be used to refer to this constraint.

REF NODE

Set this parameter equal to either the node number of the reference node or the name of a node set containing the reference nodes.

SURFACE

Set this parameter equal to the surface name on which the coupling nodes are located.

### **Optional parameters: **

INFLUENCE RADIUS

Set this parameter equal to the radius of influence centered about the reference node. If this parameter is omitted, the entire surface is used to define the coupling constraint.

ORIENTATION

Set this parameter equal to the name given to the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that specifies the initial orientation of the local system in which the constrained degrees of freedom are defined.

**There are no data lines associated with this option.**



