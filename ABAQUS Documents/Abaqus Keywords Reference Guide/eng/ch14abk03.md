# *NGEN







### *NGENGenerate incremental nodes.

This option is used to generate nodes incrementally.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Not applicable; nodes are generated when you mesh the model.

##### **Reference:**

- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

### **Optional parameters: **

LINE

Set LINE=P to generate the nodes along a parabola. In this case the user must define an extra point, the midpoint between the two end points.

Set LINE=C to generate the nodes along a circular arc. In this case the user must define an extra point, the center of the circle.

If this parameter is omitted, the nodes will be generated along a straight line.

NSET

Set this parameter equal to the name of a node set to which the nodes will be assigned. The two end nodes will also be included in the node set. Node sets created or modified with this option will always be sorted.

SYSTEM

Set SYSTEM=RC (default) to define the extra node in a Cartesian coordinate system. Set SYSTEM=C to define the extra node in a cylindrical coordinate system. Set SYSTEM=S to define the extra node in a spherical coordinate system. See [Figure 14.3--1](ch14abk03.md#kngen-1).

### **Data lines to generate nodes incrementally: **

**First line:**

Repeat this data line as often as necessary.

**Figure 14.3–1** Coordinate systems.

![](../graphics/kngen-nls.png)




