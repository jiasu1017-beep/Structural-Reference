# *CONTACT PAIR







### *CONTACT PAIRDefine surfaces that contact each other.

This option is used to define pairs of surfaces or pairs of node sets and surfaces that may contact or interact with each other during the analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Defining contact pairs in Abaqus/Standard," Section 36.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpair)
- ["Adjusting initial surface positions and specifying initial clearances in Abaqus/Standard contact pairs," Section 36.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aadjustsurfaces)
- ["Defining tied contact in Abaqus/Standard," Section 36.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-atiedcontact)
- ["Adjusting contact controls in Abaqus/Standard," Section 36.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactcontrolsstd)
- ["Contact formulations in Abaqus/Standard," Section 38.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpairform)
- ["Smoothing contact surfaces in Abaqus/Standard," Section 38.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asmoothsurfaces)
- ["Common difficulties associated with contact modeling in Abaqus/Standard," Section 39.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontacttrouble)
- ["Defining contact pairs in Abaqus/Explicit," Section 36.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aexpcontactpair)
- ["Contact formulations for contact pairs in Abaqus/Explicit," Section 38.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aexpcontactpairform)
- ["Adjusting initial surface positions and specifying initial clearances for contact pairs in Abaqus/Explicit," Section 36.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aexpadjustsurfaces)

### Defining contacting surfaces in an Abaqus/Standard analysis

### **Required parameter: **

INTERACTION

Set this parameter equal to the name of the [*SURFACE INTERACTION](ch18abk50.md) property definition associated with the contact pair being defined.

### **Optional parameters: **

ADJUST

Set this parameter equal to a node set label or a value to adjust the initial positions of the surfaces specified in this option. These adjustments are made at the start of the analysis and do not create any strain. This parameter is required for TIED contact.

EXTENSION ZONE

Set this parameter equal to a fraction of the end segment or facet edge length by which the master surface is to be extended to avoid numerical roundoff errors associated with contact modeling. The value given must lie between 0.0 and 0.2. The default is 0.1. This parameter affects only node-to-surface contact.

GEOMETRIC CORRECTION

Set this parameter equal to the name of the surface smoothing property defined by [*SURFACE SMOOTHING](ch18abk55.md). This parameter affects only surface-to-surface contact.

HCRIT

Set this parameter equal to the distance by which a point on the slave surface must penetrate the master surface before Abaqus/Standard abandons the current increment and tries again with a smaller increment. The default value of HCRIT is half of the length of a characteristic element face on the slave surface. This parameter does not apply to contact pairs that use the finite-sliding, surface-to-surface contact formulation.

MIDFACE NODES

Set MIDFACE NODES=YES to automatically convert most three-dimensional second-order element types with no midface node (serendipity elements) that form a slave surface of a surface-to-surface contact pair into elements with a midface node.

Set MIDFACE NODES=NO (default) to avoid adding midface nodes to elements underlying the slave surface of a surface-to-surface contact pair.

This parameter can be used only with surface-to-surface contact pairs. Abaqus/Standard automatically converts most serendipity elements that form a slave surface of a node-to-surface contact pair into elements with a midface node.

MINIMUM DISTANCE

Set MINIMUM DISTANCE=YES (default) to automatically activate localized contact damping when nearby surfaces are initially touching at only a single point.

 Set MINIMUM DISTANCE=NO to forgo this automatic localized damping.

This parameter can be used only with the finite-sliding, surface-to-surface contact formulation.

NO THICKNESS

Include this parameter to ignore surface thickness effects in the contact calculations. This parameter affects only contact formulations that account for surface thickness by default (it does not affect finite-sliding, node-to-surface contact).

SMALL SLIDING

Include this parameter to indicate that the small-sliding contact formulation, rather than the finite-sliding contact formulation, should be used. This parameter is not allowed with self-contact.

SMOOTH

Set this parameter equal to the degree of smoothing used for element-based master surfaces in the finite-sliding, node-to-surface contact formulation. The value given must lie between 0.0 and 0.5. The default is 0.2. This parameter does not affect contact pairs with analytical rigid surfaces or contact formulations other than the finite-sliding, node-to-surface contact formulation.

SLIDING TRANSITION

Set SLIDING TRANSITION=ELEMENT ORDER SMOOTHING to have smoothing of the nodal force redistribution upon sliding be of the same order as the elements underlying the slave surface.

Set SLIDING TRANSITION=LINEAR SMOOTHING to have linear smoothing of the nodal force redistribution upon sliding.

Set SLIDING TRANSITION=QUADRATIC SMOOTHING to have quadratic smoothing of the nodal force redistribution upon sliding.

This parameter can be used only with the surface-to-surface contact formulation.

SUPPLEMENTARY CONSTRAINTS

Set SUPPLEMENTARY CONSTRAINTS=SELECTIVE (default) to use a selective scheme of supplementary constraints.

Set SUPPLEMENTARY CONSTRAINTS=YES to add the supplementary contact constraints when applicable.

Set SUPPLEMENTARY CONSTRAINTS=NO to forgo the supplementary contact constraints.

TIED

Include this parameter to indicate that the surfaces of this [*CONTACT PAIR](ch03abk68.md) are to be “tied” together for the duration of the simulation. The ADJUST parameter is required when the TIED parameter is used. This parameter is not allowed with self-contact.

TRACKING

This parameter controls which contact tracking algorithm is used for finite-sliding, surface-to-surface contact; it has no effect on contact pairs that use other formulations.

Set TRACKING=PATH (default) to invoke a path-based contact tracking algorithm for finite-sliding, surface-to-surface contact.

Set TRACKING=STATE to invoke a state-based contact tracking algorithm for finite-sliding, surface-to-surface contact.

TYPE

Set TYPE=NODE TO SURFACE (default) to have the contact constraint coefficients generated according to the interpolation functions at the point where the slave node projects onto the master surface.

Set TYPE=SURFACE TO SURFACE to have the contact constraint coefficients generated such that stress accuracy is optimized for the specified surface type pairings. This parameter setting will be ignored for contact pairs that include a node-based surface.

### **Data lines to define the surfaces and node sets forming the contact pairs: **

**First line:**

Repeat this data line as often as necessary to define all of the surfaces or node sets forming the contact pairs. Each data line defines a pair of surfaces or a node set and a surface that may interact with one another.

### Defining contacting surfaces in an Abaqus/Explicit analysis

### **Optional parameters: **

CPSET

Set this parameter equal to the name of the contact pair set to which the contact pairs being defined should be added. The CPSET name can be used to associate contact pairs with a [*CLEARANCE](ch03abk21.md) option or with a [*CONTACT CONTROLS](ch03abk57.md) option, which can be used to adjust algorithmic control parameters. It can also be used with the [*CONTACT OUTPUT](ch03abk67.md) option to specify the contact  pairs for which output database results are desired.

INTERACTION

Set this parameter equal to the name of the [*SURFACE INTERACTION](ch18abk50.md) property definition associated with the contact pair being defined.

MECHANICAL CONSTRAINT

Set this parameter equal to the name of the method used to enforce the contact constraints.

Set MECHANICAL CONSTRAINT=KINEMATIC (default) to choose the kinematic contact method.

Set MECHANICAL CONSTRAINT=PENALTY to choose the penalty contact method.

OP

Set OP=ADD (default) to add new contact pairs to the existing set of contact pairs. Set OP=DELETE to remove the contact pairs given in this use of the option from the active set of contact pairs.

SMALL SLIDING

Include this parameter to indicate that the small-sliding contact formulation, rather than the finite-sliding contact formulation, should be used. This parameter can be used only for contact pairs that are defined in the first step of the simulation and use the kinematic constraint method.

WEIGHT

Set this parameter equal to the weighting factor for the contact surfaces.

### **Data lines to define the surfaces and node sets forming contact pairs: **

**First line:**

Repeat this data line as often as necessary to define all of the surfaces or node sets forming contact pairs. Each data line defines a pair of surfaces or a node set and a surface that may interact with one another. 




