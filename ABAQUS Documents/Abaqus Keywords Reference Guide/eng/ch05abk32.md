# *EULERIAN MESH MOTION







### *EULERIAN MESH MOTIONDefine the motion of an Eulerian mesh.

This option allows an Eulerian mesh to translate with the motion of a specified surface and expand and contract to encompass the surface's extent.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["Eulerian mesh motion," Section 14.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeulerianmeshmotion)

### **Required parameter: **

ELSET

Set this parameter equal to the element set name given on the [*EULERIAN SECTION](ch05abk33.md) definition for which to activate mesh motion.

### **Required parameter when activating mesh motion for the first time or redefining mesh motion after OP=NEW is used: **

SURFACE

Set this parameter equal to the name of a node-based, element-based, or Eulerian material surface used to control the motion of the Eulerian mesh.

### **Optional parameters: **

ASPECT RATIO MAX

Set this parameter equal to the maximum change in the allowed aspect ratio of any of the three bounding box aspects (1–2, 2–3, 3–1). The default is 10.0.

BUFFER

Set this parameter equal to a value to maintain a buffer between the bounding box and surface equal to the value times the maximum Eulerian element size in the mesh. The default is BUFFER=2.0.

Set BUFFER=INITIAL to maintain the initial scaling of the mesh with respect to the surface.

CENTER

Set CENTER=BOUNDING BOX (default) to align the center of the bounding box with the center of the surface's bounding box.

Set CENTER=MASS to align the center of the bounding box with the center of mass of the surface.

CONTRACT

Set CONTRACT=YES (default) to allow the bounding box to contract during the analysis.

Set CONTRACT=NO to disallow contraction of the bounding box.

OP

Set OP=MOD (default) to modify existing mesh motion options or to define additional mesh motion options for the given element set.

Set OP=NEW to remove or overwrite an existing mesh motion definition for the given element set.

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used to define the local directions of the bounding box. Only orientations defined with SYSTEM=RECTANGULAR or SYSTEM=Z RECTANGULAR can be specified.

VMAX FACTOR

Set this parameter equal to a fraction of the maximum velocity of the surface nodes to bound the mesh motion velocity. The default is VMAX FACTOR=1.01.

VOLFRAC MIN

Set this parameter equal to the lower bound on the volume fraction used to determine which nodes to include in the bounding box calculation for an Eulerian material surface. The default is VOLFRAC MIN=0.5.

### **Optional data lines to define bounding box constraints: **

**First line:**

**Second line:**

**Third line:**




