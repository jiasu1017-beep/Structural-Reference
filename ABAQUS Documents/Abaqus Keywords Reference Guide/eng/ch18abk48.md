# *SURFACE BEHAVIOR







### *SURFACE BEHAVIORDefine alternative pressure-overclosure relationships for contact.

This option is used to modify the default hard contact pressure-overclosure relationship in a mechanical contact analysis. Mechanical interactions normal to the surfaces are influenced by this option. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option or in an Abaqus/Standard analysis with the [*GAP](ch07abk01.md) option or the [*INTERFACE](ch09abk22.md) option. By default, Abaqus/Standard will determine whether the contact constraint will be enforced with or without a Lagrange multiplier. You can use the [*CONTACT CONTROLS](ch03abk57.md) option to override the default.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; Model or history data in Abaqus/Explicit  

**Level: **Part,  Part instance,  Assembly,  Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Mechanical contact properties: overview," Section 37.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["Contact pressure-overclosure relationships," Section 37.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-anormalinteraction)
- [*CONTACT CONTROLS](ch03abk57.md)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)

### **Optional, mutually exclusive parameters: **

AUGMENTED LAGRANGE

This parameter applies only to Abaqus/Standard analyses with a default “hard” pressure-overclosure relationship. 

Include this parameter to choose the augmented Lagrange method for enforcement of the contact constraint. See ["Contact constraint enforcement methods in Abaqus/Standard," Section 38.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactconstraints), for a discussion of the default penalty stiffness and penetration tolerance associated with this method (the default penalty stiffness used by this method is often stiffer than that with the straight penalty method). You can specify or modify the penalty stiffness on the data line.

DIRECT

This parameter applies only to Abaqus/Standard analyses. 

Include this parameter to choose direct enforcement of contact constraints without approximation or use of augmentation iterations.

PENALTY

This parameter applies only to Abaqus/Standard analyses with a default “hard” pressure-overclosure relationship. 

Set PENALTY=LINEAR (default) to choose the linear penalty method for enforcement of the contact constraint. See ["Contact constraint enforcement methods in Abaqus/Standard," Section 38.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactconstraints), for a discussion of the default linear penalty stiffness. You can specify or modify the penalty stiffness on the data line.

Set PENALTY=NONLINEAR to choose the nonlinear penalty method for enforcement of the contact constraint. See ["Contact constraint enforcement methods in Abaqus/Standard," Section 38.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactconstraints), for a discussion of the default nonlinear penalty stiffness. You can specify or modify the final nonlinear penalty stiffness and other nonlinear penalty control parameters on the data line.

### **Optional parameters: **

NO SEPARATION

Include this parameter to prevent any separation of the two surfaces once contact has been established.

PRESSURE-OVERCLOSURE

Use this parameter to choose a contact pressure-overclosure relationship other than the default hard contact.

Set PRESSURE-OVERCLOSURE=HARD (default) to choose a pressure-overclosure relationship without physical softening. Note that some numerical softening will occur if a penalty or augmented Lagrange constraint enforcement method is used.

Set PRESSURE-OVERCLOSURE=EXPONENTIAL to define an exponential pressure-overclosure relationship.

Set PRESSURE-OVERCLOSURE=LINEAR to define a linear pressure-overclosure relationship.

Set PRESSURE-OVERCLOSURE=SCALE FACTOR to define a piecewise linear pressure-overclosure relationship based on scaling the default contact stiffness. This option is available only for the general contact algorithm in Abaqus/Explicit.

Set PRESSURE-OVERCLOSURE=TABULAR to define a piecewise linear pressure-overclosure relationship in tabular form.

If a contact area is not defined, such as may occur for node-based surfaces or for GAP- or ITT-type contact elements, “pressure” should be interpreted as force. For contact with three-dimensional beams or trusses, “pressure” should be interpreted as force per unit length.

When used to modify the default surface behavior, the PRESSURE-OVERCLOSURE parameter cannot be used with the NO SEPARATION parameter in an Abaqus/Standard analysis.

### **Optional data line for AUGMENTED LAGRANGE and PENALTY=LINEAR: **

**First (and only) line:**

### **Optional data line for PENALTY=NONLINEAR: **

**First (and only) line:**

### **Data line for PRESSURE-OVERCLOSURE=EXPONENTIAL: **

**First (and only) line:**

### **Data line for PRESSURE-OVERCLOSURE=LINEAR: **

**First (and only) line:**

### **Data line for PRESSURE-OVERCLOSURE=SCALE FACTOR: **

**First (and only) line:**

### **Data lines for PRESSURE-OVERCLOSURE=TABULAR: **

**First line:**

Repeat this data line in ascending order of overclosure value as often as necessary to define the overclosure as a function of pressure. A minimum of two data lines are required. The pressure-overclosure relationship is extrapolated beyond the last overclosure point by continuing the same slope (see [Figure 18.48--4](ch18abk48.md#ksurfacebehavior-soft1)).

**Figure 18.48–1** Nonlinear penalty pressure-overclosure relationship.

![](../graphics/exx-surface-behavior-nonlpen1-nls.png)

**Figure 18.48–2** Exponential pressure-overclosure relationship.

![](../graphics/exxsurfacebehavior-soft-nls.png)

**Figure 18.48–3** Scale factor pressure-overclosure relationship.

![](../graphics/exxsurfacebehavior-scalefac-nls.png)

**Figure 18.48–4** Pressure-overclosure relationship defined in tabular form.

![](../graphics/ksurfacebehavior-soft1-nls.png)




