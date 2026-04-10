# *RIGID SURFACE







### *RIGID SURFACEDefine an analytical rigid surface.

This option must be used when defining the seabed for three-dimensional drag chain elements in Abaqus/Standard analyses. For all other cases the preferred options for defining analytical rigid surfaces are the [*SURFACE](ch18abk47.md) and the [*RIGID BODY](ch17abk18.md) options. 

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Part module

##### **References:**

- ["Surfaces: overview," Section 2.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-asurfoverview)
- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)
- ["Drag chains," Section 32.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-edragchain)
- ["RSURFU," Section 1.1.16 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ursurfu)
- [*SURFACE](ch18abk47.md)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the IRS-type elements or the three-dimensional drag chain elements that may interact with the rigid surface being defined.

The ELSET and NAME parameters are mutually exclusive.

NAME

Set this parameter equal to a label that will be used to refer to the rigid surface being created. This surface name is used to define contact interaction with another surface through the [*CONTACT PAIR](ch03abk68.md) option.

The ELSET and NAME parameters are mutually exclusive.

REF NODE

Set this parameter equal to either the node number of the rigid body reference node or the name of a node set containing the rigid body reference node. If the name of a node set is chosen, the node set must contain exactly one node.

This parameter is relevant only when the NAME parameter is used.

TYPE

Set TYPE=SEGMENTS to create a two-dimensional rigid surface in the ![](../graphics/key_eqn01033.gif) plane for planar models or in the ![](../graphics/key_eqn01034.gif) plane for axisymmetric models by defining connected line segments.

Set TYPE=CYLINDER to define a three-dimensional rigid surface by providing connected line segments and then sweeping them along a specified generator vector.

Set TYPE=REVOLUTION to define a three-dimensional rigid surface by providing connected line segments, which are given in an ![](../graphics/key_eqn01034.gif) plane and are rotated about an axis.

Set TYPE=USER to define a rigid surface via user subroutine [`RSURFU`](../sub/sub-link.md#sub-xsl-rsurfu).

### **Optional parameter: **

FILLET RADIUS

This parameter can be used with TYPE=SEGMENTS, TYPE=CYLINDER, or TYPE=REVOLUTION to define a radius of curvature to smooth discontinuities between adjoining straight-line segments, adjoining circular-arc segments, and adjoining straight-line and circular-arc segments. It has no effect on rigid surfaces defined with TYPE=USER.

### **No data lines are needed for TYPE=USER. **

### **Data lines to define surfaces created with TYPE=SEGMENTS: **

**First line:**

Second and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the rigid surface.

### **Data lines to define surfaces created with TYPE=CYLINDER: **

**First line:**

**Second line:**

**Third line:**

Fourth and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the rigid surface.

### **Data lines to define surfaces created with TYPE=REVOLUTION: **

**First line:**

**Second line:**

Third and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the rigid surface.

### **Data lines that define the line segments that form the rigid surface for TYPE=SEGMENTS, TYPE=CYLINDER, and TYPE=REVOLUTION: **

**Data line to define a straight line segment:**

**Data line to define a circular arc segment (the arc must be less than 180):**

**Data line to define a parabolic arc segment:**

For rigid surfaces created with TYPE=SEGMENTS, the *x*- and *y*-coordinates are the global *X*- and *Y*-coordinates or *r*- and *z*-coordinates. For rigid surfaces created with TYPE=CYLINDER, the *x*- and *y*-coordinates are the local *x*- and *y*-coordinates. For rigid surfaces created with TYPE=REVOLUTION, the *x*- and *y*-coordinates are the local *r*- and *z*-coordinates.

**Figure 17.19–1** [*RIGID SURFACE](ch17abk19.md), TYPE=CYLINDER.

![](../graphics/krigidsurface-cylinder-nls.png)

**Figure 17.19–2** [*RIGID SURFACE](ch17abk19.md), TYPE=REVOLUTION.

![](../graphics/krigidsurface-rev-nls.png)




