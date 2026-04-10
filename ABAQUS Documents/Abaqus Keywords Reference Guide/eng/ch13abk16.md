# *MEMBRANE SECTION







### *MEMBRANE SECTIONSpecify section properties for membrane elements.

This option is used to assign section properties to a set of membrane elements. Section properties include thickness, thickness change behavior, material definition, and material orientation.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Membrane elements," Section 29.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-emembrane)
- [*DISTRIBUTION](ch04abk29.md)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the membrane elements for which the section properties are being defined.

MATERIAL

Set this parameter equal to the name of the material to be used with these elements.

### **Optional parameters: **

CONTROLS

In an Abaqus/Explicit analysis, set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify a nondefault hourglass control formulation option or scale factors.

In an Abaqus/Standard analysis, set this parameter equal to the name of a section controls definition to be used to specify the enhanced hourglass control formulation (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) or to be used in a subsequent Abaqus/Explicit import analysis.

DENSITY

Set this parameter equal to a mass per unit surface area of the membrane.

If this parameter is used, the mass of the membrane includes a contribution from this parameter in addition to any contribution from the material definition.

MEMBRANE THICKNESS

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)) to define spatially varying thickness.

The distribution used to define membrane thickness must have a default value. The default thickness is used by any membrane element assigned to the membrane section that is not specifically assigned a value in the distribution.

The NODAL THICKNESS and MEMBRANE THICKNESS parameters are mutually exclusive.

NODAL THICKNESS

Include this parameter to indicate that the membrane thickness should not be read from the data lines but should be interpolated from the thickness specified at the nodes with the [*NODAL THICKNESS](ch14abk08.md) option.

The NODAL THICKNESS and MEMBRANE THICKNESS parameters are mutually exclusive.

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option to be used to define a local coordinate system for material calculations in the elements in this set.

POISSON

This parameter is relevant only in a large-deformation analysis. Set it equal to a nonzero value to cause the thickness to change as a function of membrane strains. The value of the POISSON parameter must be between 1.0 and 0.5. A value of 0.5 will enforce incompressible behavior of the element. POISSON=0.0 means that the thickness will not change.

Set this parameter equal to MATERIAL in an Abaqus/Explicit analysis to cause the thickness to change based on the element material definition.

The default is POISSON=0.5 in Abaqus/Standard and POISSON=MATERIAL in Abaqus/Explicit.

### **Data line for a constant thickness membrane: **

**First (and only) line:**

### **To define a continuously varying thickness membrane: **

No data lines are used with this option when the NODAL THICKNESS or MEMBRANE THICKNESS parameters are specified; any value input on the data line will be ignored. Instead, the [*NODAL THICKNESS](ch14abk08.md) or MEMBRANE THICKNESS option is used to define the section thickness.




