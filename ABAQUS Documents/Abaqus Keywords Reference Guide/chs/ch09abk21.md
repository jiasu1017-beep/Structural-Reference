# *INTEGRATED OUTPUT SECTION







### *INTEGRATED OUTPUT SECTIONDefine an integrated output section over a surface with a local coordinate system and a reference point.

This option is used to associate a surface with a coordinate system and/or a reference node to track the average motion of the surface. It can also be used in conjunction with an integrated output request to obtain output of quantities integrated over a surface.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Step module

##### **References:**

- ["Integrated output section definition," Section 2.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aintegratedoutputsect)
- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*INTEGRATED OUTPUT](ch09abk20.md)
- [*SURFACE](ch18abk47.md)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to refer to the integrated output section.

SURFACE

Set this parameter equal to the name of the surface (see ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)) to be associated with the integrated output section.

### **Optional parameters: **

ORIENTATION

Set this parameter equal to the name of an orientation definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to define the initial coordinate system for the section. This initial system can be further modified by using the PROJECT ORIENTATION parameter.

If this parameter is omitted, the global coordinate system is used.

POSITION

This parameter is relevant only if the REF NODE parameter is included. 

Set POSITION=INPUT (default) if the location of the reference node is to be defined by the user.

Set POSITION=CENTER if the reference node is to be relocated from the user-defined location to the center of the surface in the initial configuration.

PROJECT ORIENTATION

Set PROJECT ORIENTATION=NO (default) if the initial coordinate system of the section should not be projected onto the section surface. If the ORIENTATION parameter is included, this choice results in an initial coordinate system that matches the defined orientation. If an orientation is not specified, the initial coordinate system matches the global coordinate system.

Set PROJECT ORIENTATION=YES if the initial coordinate system of the section should be modified by projecting onto the section surface using the average normal to the surface. If an orientation is not specified, the global coordinate system is projected onto the section surface.

REF NODE

Set this parameter equal to either the node number of the integrated output section reference node or to the name of a node set containing the reference node. If the name of a node set is chosen, the node set must contain exactly one node.

REF NODE MOTION

This parameter is relevant only if the REF NODE parameter is included.

Set REF NODE MOTION=INDEPENDENT (default) if the motion of the reference node is not based on the average motion of the surface.

Set REF NODE MOTION=AVERAGE TRANSLATION if the reference node must translate with the average translation of the surface. This choice is relevant only if the reference node is not connected to the rest of the model.

Set REF NODE MOTION=AVERAGE  if the reference node must both translate and rotate with the average motion of the surface. This choice is relevant only if the reference node is not connected to the rest of the model.

**There are no data lines associated with this option.**



