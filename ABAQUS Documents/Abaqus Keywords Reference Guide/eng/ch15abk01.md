# *ORIENTATION







### *ORIENTATIONDefine a local axis system for material or element property definition, for kinematic coupling constraints, for free directions for inertia relief loads, or for connectors.

This option is used to define a local coordinate system for definition of material properties; for material calculations at integration points; for element property definitions (e.g., connector elements); for output of components of stress, strain, and element section forces; and for kinematic and distributing coupling constraints. A spatially varying local coordinate system can be defined for  solid continuum elements and shell elements using distributions (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

The [*ORIENTATION](ch15abk01.md) option can also be used to specify local material directions for anisotropic hyperelastic materials with invariant-based formulation (["Invariant-based formulation" in "Anisotropic hyperelastic behavior," Section 22.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-canisohyperelastic-invbased)). The local directions are defined with respect to the local coordinate system.

In Abaqus/Standard the [*ORIENTATION](ch15abk01.md) option can be used to define local directions for contact pair interaction properties and spring, dashpot, and JOINTC elements; for definition of local free directions for inertia relief loads; and for output of components of surface variables.

In Abaqus/Explicit the [*ORIENTATION](ch15abk01.md) option can be used to initialize the directions of the fill and the warp yarns of a fabric material in the reference configuration. The yarn directions lying in the plane of the fabric are defined with respect to the two in-plane axes of the orthogonal coordinate system. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module, Interaction module, and Pub _nolinebreak?LoadPub /_nolinebreak? module

##### **References:**

- ["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)
- ["ORIENT," Section 1.1.15 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uorient)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the orientation definition. Orientation names in the same input file must be unique.

### **Optional parameters: **

DEFINITION

Set DEFINITION=COORDINATES (default) to define the local system by giving the coordinates of the three points *a*, *b*, and, optionally, *c* (the origin) appropriate to the SYSTEM choice from [Figure 15.1--1](ch15abk01.md#korientation). A spatially varying local coordinate system can be created for solid continuum elements and shell elements for this parameter value by using a distribution to define spatially varying coordinates for points *a* and *b*. Using a distribution to define the coordinates of the optional point *c* is not currently supported. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions).

Set DEFINITION=NODES to define the local system by giving global node numbers for points *a*, *b*, and, optionally, *c* (the origin).

Set DEFINITION=OFFSET TO NODES to define the local system by giving local node numbers (on the element where the orientation is being used) to define the points *a*, *b*, and, optionally, *c* (the origin) in [Figure 15.1--1](ch15abk01.md#korientation). This parameter value cannot be used with spring, dashpot, or JOINTC elements. In addition, it cannot be used with the [*KINEMATIC COUPLING](ch11abk03.md), [*INERTIA RELIEF](ch09abk17.md), or [*CONTACT PAIR](ch03abk68.md) options.

For all DEFINITION parameter values a spatially varying local coordinate system can be created for solid continuum elements and shell elements by using a distribution to define a spatially varying additional rotation angle ![](../graphics/key_eqn00080.gif). See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions). 

LOCAL DIRECTIONS

This parameter is relevant only for anisotropic materials with preferred material directions (or fiber directions), such as anisotropic hyperelastic materials or, in Abaqus/Explicit, fabric materials.

 Set this parameter equal to the number of local directions that are applicable to the material model (for example, two for a fabric material). The local directions are specified with respect to the orthonormal system at the material point resulting from the current orientation definition.  Up to three local directions can be specified as part of the definition of a local orientation system. 

For the fabric material in Abaqus/Explicit, the two yarn directions are given with respect to the in-plane axes of the orthonormal system. If no local directions are specified as part of the orientation definition, the local material directions are assumed to match the in-plane axes of the orthonormal system in the reference configuration.

SYSTEM

Set SYSTEM=RECTANGULAR (default) to define a rectangular Cartesian system by the three points *a*, *b*, and *c* shown in [Figure 15.1--1](ch15abk01.md#korientation). Point *c* is the origin of the system, point *a* must lie on the  ![](../graphics/key_eqn00927.gif)-axis, and point *b* must lie on the  ![](../graphics/key_eqn00927.gif)-![](../graphics/key_eqn00928.gif) plane. Although not necessary, it is intuitive to select point *b* such that it is on or near the local ![](../graphics/key_eqn00928.gif)-axis.

Set SYSTEM=CYLINDRICAL to define a cylindrical system by giving the two points *a* and *b* on the polar axis of the cylindrical system ([Figure 15.1--1](ch15abk01.md#korientation)). The local axes are 1=radial, 2=circumferential, 3=axial.

Set SYSTEM=SPHERICAL to define a spherical system by giving the center of the sphere, *a*, and point *b* on the polar axis ([Figure 15.1--1](ch15abk01.md#korientation)). The local axes are 1=radial, 2=circumferential, 3=meridional.

Set SYSTEM=Z RECTANGULAR to define a rectangular Cartesian system by the three points *a*, *b*, and *c* shown in [Figure 15.1--1](ch15abk01.md#korientation).  Point *c* is the origin of the system, point *a* must lie on the  ![](../graphics/key_eqn00929.gif)-axis, and point *b* must lie on the  ![](../graphics/key_eqn00927.gif)-![](../graphics/key_eqn00929.gif) plane. Although not necessary, it is intuitive to select point *b* such that it is on or near the local ![](../graphics/key_eqn00927.gif)-axis.

Set SYSTEM=USER in an Abaqus/Standard analysis to define the local coordinate system in user subroutine [`ORIENT`](../sub/sub-link.md#sub-xsl-orient). The DEFINITION parameter and any data lines associated with the option are ignored if SYSTEM=USER.

### **Data lines to define an orientation using DEFINITION=COORDINATES: **

**First line:**

**Second line:**

**Third line when the LOCAL DIRECTIONS parameter is included:**

Repeat the above data line to define additional local directions, as needed, with each direction on a separate line.

### **Data lines to define a spatially varying orientation for solid continuum and shell elements using a distribution when DEFINITION=COORDINATES: **

**First line:**

**Second line:**

**Third line when the LOCAL DIRECTIONS parameter is included:**

Repeat the above data line to define additional local directions, as needed, with each direction on a separate line.

### **Data lines to define an orientation using DEFINITION=NODES: **

**First line:**

**Second line:**

**Third line when the LOCAL DIRECTIONS parameter is included:**

Repeat the above data line to define additional local directions, as needed, with each direction on a separate line.

### **Data lines to define an orientation using DEFINITION=OFFSET TO NODES: **

**First line:**

**Second line:**

**Third line when the LOCAL DIRECTIONS parameter is included:**

Repeat the above data line to define additional local directions, as needed, with each direction on a separate line.

### **To define an orientation using a user subroutine (SYSTEM=USER): **

No data lines are used with this option when SYSTEM=USER is specified. Instead, user subroutine [`ORIENT`](../sub/sub-link.md#sub-xsl-orient) must be used to define the orientation.

**Figure 15.1–1** Orientation systems.

![](../graphics/korientation-nls.png)




