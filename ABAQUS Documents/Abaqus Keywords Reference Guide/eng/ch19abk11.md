# *TRANSFORM







### *TRANSFORMSpecify a local coordinate system at nodes.

This option is used to specify a local coordinate system for displacement and rotation degrees of freedom at a node.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Define nodal coordinate systems for prescribed conditions in the Load module.

##### **Reference:**

- ["Transformed coordinate systems," Section 2.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ptransform)

### **Required parameter: **

NSET

Set this parameter equal to the name of the node set for which the local transformed system is being given.

### **Optional parameter: **

TYPE

Set TYPE=R (default) to indicate a rectangular Cartesian system ([Figure 19.11--1](ch19abk11.md#ktransform-cartesian)). Set TYPE=C to indicate a cylindrical system ([Figure 19.11--2](ch19abk11.md#ktransform-cylindrical)). Set TYPE=S to indicate a spherical system ([Figure 19.11--3](ch19abk11.md#ktransform-spherical)).

### **Data line to define a transformed coordinate system: **

**First (and only) line:**

**Figure 19.11–1** Cartesian transformation option.

![](../graphics/ktransform-cartesian-nls.png)

**Figure 19.11–2** Cylindrical transformation option.

![](../graphics/ktransform-cylindrical-nls.png)

**Figure 19.11–3** Spherical transformation option.

![](../graphics/ktransform-spherical-nls.png)




