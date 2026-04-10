# *ADJUST







### *ADJUSTAdjust user-specified nodal coordinates to lie on a given surface.

This option is used to adjust user-specified nodal coordinates so that the nodes lie on a given surface.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Adjusting nodal coordinates," Section 2.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-madjust)

### **Required parameters: **

NODE SET

Set this parameter equal to the name of the node set containing the nodes to be adjusted.

SURFACE

Set this parameter equal to the name of surface to which the nodes are to be adjusted. 

### **Optional parameter: **

ORIENTATION

Set this parameter equal to the name of an orientation definition (see ["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that defines the direction for adjusting nodes. If this parameter is omitted, the nodes are adjusted normal to the specified surface. Only rectangular, cylindrical, and spherical orientation definitions are supported. Additional rotations defined as part of the orientation definition are ignored. 

**There are no data lines associated with this option.**



