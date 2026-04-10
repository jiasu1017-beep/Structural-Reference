# *SOLID SECTION







### *SOLID SECTIONSpecify element properties for solid, infinite, acoustic, particle, and truss elements.

This option is used to define properties of solid (continuum) elements, infinite elements, acoustic finite and infinite elements, particle elements, and truss elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Solid (continuum) elements," Section 28.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esolidcont)
- ["Infinite elements," Section 28.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-einfinite)
- ["Continuum particle elements," Section 33.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esphelem)
- ["Truss elements," Section 29.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-etruss)

### **Required parameters: **

COMPOSITE

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used only with three-dimensional brick solid elements that have only displacement degrees of freedom. Include this parameter if the solid is made up of several layers of material.

The COMPOSITE and MATERIAL parameters are mutually exclusive.

ELSET

Set this parameter equal to the name of the element set containing the elements for which the material behavior is being defined.

MATERIAL

Set this parameter equal to the name of the material to be used with these elements.

The COMPOSITE and MATERIAL parameters are mutually exclusive.

REF NODE

This parameter is required only for generalized plane strain elements and acoustic infinite elements; it is ignored for all other element types.

Set this parameter equal to either the node number of the reference node or the name of a node set containing the reference node. If the name of a node set is chosen, the node set must contain exactly one node.

### **Required parameter for anisotropic materials; optional parameter for isotropic materials: **

ORIENTATION

Set this parameter equal to the name of an orientation definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used to define a local coordinate system for material calculations in the elements in this set. This parameter is required when the material is anisotropic. 

For a composite solid this orientation, together with the orientation angle specified on the layer data lines, can also be used to define the material orientations in the individual layers. Alternatively, a material orientation can be specified by referencing an orientation definition on each layer data line. In this case the reference given on the ORIENTATION parameter is ignored. Any layer definition line that does not have an orientation reference or an angle specified will use the section orientation defined on the keyword line.

### **Optional parameters: **

CONTROLS

In an Abaqus/Explicit analysis, set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify a nondefault hourglass control formulation option or scale factor. The [*SECTION CONTROLS](ch18abk01.md) option can be used to select the hourglass control and order of accuracy of the formulation for two- and three-dimensional solid elements and to select the kinematic formulation for 8-node brick elements.

In an Abaqus/Standard analysis, set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify the enhanced hourglass control formulation or to be used in a subsequent Abaqus/Explicit import analysis.

LAYUP

This parameter is relevant only when the COMPOSITE parameter is used.

Set this parameter equal to the name of a composite layup (see [Chapter 23, "Composite layups," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-layups)). Abaqus/CAE uses this name to identify the composite layup that contains the solid section. 

ORDER

This parameter can be used only with acoustic infinite elements in Abaqus/Explicit. It defines the number of ninth-order polynomials that will be used to resolve the variation of the acoustic field in the infinite direction. Set this parameter equal to *N* to indicate that the first *N* members of the set of ninth-order polynomials are to be used. The default is ORDER=10, which is the value always used in Abaqus/Standard.

STACK DIRECTION

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used only with composite elements. It defines the stacking direction with respect to a pair of element faces. Set this parameter equal to 1, 2, or 3. The default is STACK DIRECTION=3.

SYMMETRIC

This parameter is relevant only when the COMPOSITE parameter is used.

Include this parameter if the layers in the composite shell are symmetric about a central core. This parameter cannot be used if spatially varying orientation angles are defined on any composite layer using distributions (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

### **Data line to define homogeneous solid elements, infinite elements, acoustic elements, particle, or truss elements: **

**First (and only) line:**

### **Data lines to define a composite solid: **

**First line:**

Repeat this data line as often as necessary to define the properties for each layer of the composite solid. If the SYMMETRIC parameter is included, specify only half the layers, from the bottom layer to the midplane.




