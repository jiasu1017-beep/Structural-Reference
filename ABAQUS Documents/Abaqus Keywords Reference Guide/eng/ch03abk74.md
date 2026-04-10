# *CONTOUR INTEGRAL







### *CONTOUR INTEGRALProvide contour integral estimates.

**Warning:**Contour integrals are not calculated accurately for the bending stress in shells. If contour integral values are needed where the bending stress is significant, use second-order solid elements (C3D20 or C3D27) in the crack-tip region where the integral is evaluated instead of shell elements. Contour integrals should not be requested in a linear perturbation step. Initial stresses are not included in the evaluation of the *J*-integrals, the stress intensity factors, and the *T*-stress (see ["Contour integral evaluation," Section 11.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acontintegral), for details).

The [*CONTOUR INTEGRAL](ch03abk74.md) option offers the evaluation of the *J*-integral, the ![](../graphics/key_eqn00378.gif)-integral, the stress intensity factors, and the *T*-stress for fracture mechanics studies based on either the conventional finite element method or the extended finite element method (XFEM). The option also computes the crack propagation direction at initiation when the stress intensity factors are evaluated. Contour integrals along several different crack fronts can be evaluated by repeating this option as often as needed in the step definition.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Contour integral evaluation," Section 11.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acontintegral)

- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Required parameter: **

CONTOURS

Set this parameter equal to the number of contours to be used. Each contour provides an evaluation of the contour integral.

### **Optional parameters: **

CRACK NAME

Set this parameter equal to a label that will be used to refer to the crack. When the extended finite element method is used, set this parameter equal to the name assigned to the enriched feature on the [*ENRICHMENT](ch05abk25.md) option.

CRACK TIP NODES

Include this parameter to indicate that the crack tip nodes are specified to form the crack front line. If this parameter is omitted, the crack front line will be formed along the first nodes of the crack front node sets. (The first node will be the node with the smallest node number for each crack front node set, unless the node set is generated as unsorted.) 

This parameter is not relevant when the XFEM parameter is specified.

DIRECTION

This parameter can be used only in combination with the TYPE=K FACTORS parameter.

Set DIRECTION=MTS (default) to choose the maximum tangential stress criterion. 

Set DIRECTION=MERR to choose the maximum energy release rate criterion. 

Set DIRECTION=KII0 to choose the ![](../graphics/key_eqn00379.gif) criterion. 

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

NORMAL

Include this parameter to indicate that the direction normal to the plane of the crack ![](../graphics/key_eqn00380.gif) is specified. Omit this parameter to indicate that the virtual crack extension direction ![](../graphics/key_eqn00381.gif) is specified. 

This parameter is not relevant when the XFEM parameter is specified.

OUTPUT

If this parameter is omitted, the contour integral values will be printed in the data (`.dat`) file but not stored in the results (`.fil`) file.

Set OUTPUT=FILE to store the contour integral values in the results file.

Set OUTPUT=BOTH to print the contour integral values in the data file and to store them in the results file.

RESIDUAL STRESS STEP

Use this parameter to account for the effect of residual stress gradients on the contour integral evaluation. Set this parameter equal to the step number from which the stress data in the last available increment of the specified step will be considered as residual stresses. The default is 0, in which case the residual stresses are defined by the specified initial conditions.

This parameter can be set equal to zero only when the XFEM parameter is specified.

SYMM

Include this parameter to indicate that the crack front is defined on a symmetry plane, with only half the structure modeled. The change in potential energy calculated from the virtual crack front advance is then doubled to compute the correct contour integral values. 

This parameter is not relevant when the XFEM parameter is specified.

TYPE

Set TYPE=J (default) to specify *J*-integral calculations. 

Set TYPE=C to specify ![](../graphics/key_eqn00378.gif)-integral calculations. 

Set TYPE=K FACTORS to specify the calculations of the stress intensity factors. 

Set TYPE=T-STRESS to specify the *T*-stress calculations.

XFEM

Include this parameter to indicate that the crack is modeled as an enriched feature with the extended finite element method.

### **Data lines if the NORMAL parameter is included but the CRACK TIP NODES and XFEM parameters are both omitted: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define the crack front node sets. Up to 16 entries are allowed per line.

### **Data lines if the NORMAL, CRACK TIP NODES, and XFEM parameters are all omitted: **

**First line:**

In two-dimensional cases only one data line is necessary. In three-dimensional cases repeat this data line as often as necessary to define the crack front node sets and virtual crack extension vectors along the crack front.

### **Data lines if the NORMAL and CRACK TIP NODES parameters are both included but the XFEM parameter is omitted: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define the crack front.

### **Data lines if the NORMAL and XFEM parameters are both omitted but the CRACK TIP NODES parameter is included: **

**First line:**

In two-dimensional cases only one data line is necessary. In three-dimensional cases repeat this data line as often as necessary to define the crack front node sets and virtual crack extension vectors along the crack front.

### **No data lines are needed if the XFEM parameter is included. **




