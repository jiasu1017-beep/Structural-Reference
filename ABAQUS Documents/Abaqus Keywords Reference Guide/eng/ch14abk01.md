# *NCOPY







### *NCOPYCreate nodes by copying.

This option is used to copy a node set to create a new node set.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Not applicable; copying portions of sketches and instancing of parts serve similar purposes.

##### **Reference:**

- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

### **Required parameters: **

CHANGE NUMBER

Set this parameter equal to an integer that will be added to each of the existing node numbers to define the node numbers of the nodes being created.

OLD SET

Set this parameter equal to the name of the node set being copied. This set will be used for the copy operation with the nodes that belong to it at the time this [*NCOPY](ch14abk01.md) option appears in the input file.

### **Required, mutually exclusive parameters: **

POLE

Include this parameter if the new nodes are created by projecting the nodes in the old set from the pole node. Each new node will be located such that the corresponding old node is equidistant between the pole node and the new node.

This parameter is particularly useful for creating nodes associated with infinite elements (["Infinite elements," Section 28.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-einfinite)).

REFLECT

Set REFLECT=LINE to create the new nodes by reflection through a line. 

Set REFLECT=MIRROR to create the new nodes by reflection through a plane. 

Set REFLECT=POINT to create the new nodes by reflection through a point.

SHIFT

Include this parameter if the new nodes are to be created by translation and/or rotation of the nodes in the old node set. If both translation and rotation are specified, the translation is applied once before the rotation.

### **Optional parameters: **

MULTIPLE

This parameter is used with the SHIFT parameter to define the number of times the rotation should be applied. The default is MULTIPLE=1.

NEW SET

Set this parameter equal to the name of the node set to which the nodes created by the operation will be assigned. This new node set will be unsorted if the OLD SET was unsorted and if the NEW SET does not already exist. Otherwise, this new node set will be a sorted set.

If this parameter is omitted, the newly created nodes are not assigned to a node set.

### **Data lines if the SHIFT parameter is included: **

**First line:**

**Second line:**

### **Data line if REFLECT=LINE: **

**First (and only) line:**

### **Data lines if REFLECT=MIRROR: **

**First line:**

**Second line:**

### **Data line if REFLECT=POINT: **

**First (and only) line:**

### **Data line if the POLE parameter is included: **

**First (and only) line:**

**Figure 14.1–1** [*NCOPY](ch14abk01.md), SHIFT option.

![](../graphics/kncopy-shift-nls.png)

**Figure 14.1–2** [*NCOPY](ch14abk01.md), REFLECT=LINE option.

![](../graphics/kncopy-reflect-line-nls.png)

**Figure 14.1–3** [*NCOPY](ch14abk01.md), REFLECT=MIRROR option.

![](../graphics/kncopy-reflect-mirror-nls.png)

**Figure 14.1–4** [*NCOPY](ch14abk01.md), REFLECT=POINT option.

![](../graphics/kncopy-reflect-point-nls.png)

**Figure 14.1–5** [*NCOPY](ch14abk01.md), POLE option.

![](../graphics/kncopy-pole-nls.png)




