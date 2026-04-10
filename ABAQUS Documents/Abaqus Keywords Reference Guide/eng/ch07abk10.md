# *GASKET ELASTICITY







### *GASKET ELASTICITYSpecify elastic properties for the membrane and transverse shear behaviors of a gasket.

This option is used to define the elastic parameters for the membrane and transverse shear behaviors of a gasket.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Defining the gasket behavior directly using a gasket behavior model," Section 32.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketbehavior)

### **Optional parameters: **

COMPONENT

Set COMPONENT=MEMBRANE to define the membrane behavior of a gasket.

Set COMPONENT=TRANSVERSE SHEAR (default) to define the transverse shear behavior of a gasket.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the elastic parameters, in addition to temperature. If this parameter is omitted, it is assumed that the elastic parameters depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

VARIABLE

This parameter is used only with COMPONENT=TRANSVERSE SHEAR to specify the unit system in which the transverse shear behavior will be defined.

Set VARIABLE=FORCE to define the transverse shear stiffness in terms of force per unit displacement or force per unit length per unit displacement, depending on the element type to which this behavior refers.

Set VARIABLE=STRESS (default) to define the transverse shear stiffness in terms of stress per unit displacement.

### **Data lines for COMPONENT=TRANSVERSE SHEAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the shear stiffness on temperature and field variables.

### **Data lines for COMPONENT=MEMBRANE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of Young's modulus and Poisson's ratio on temperature and field variables.




