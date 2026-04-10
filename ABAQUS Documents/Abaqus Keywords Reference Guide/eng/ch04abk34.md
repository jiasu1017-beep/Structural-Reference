# *DRUCKER PRAGER







### *DRUCKER PRAGERSpecify the extended Drucker-Prager plasticity model.

This option is used to define yield surface and flow potential parameters for elastic-plastic materials that use one of the extended Drucker-Prager plasticity models. It must be used in conjunction with the [*DRUCKER PRAGER HARDENING](ch04abk36.md) option and, if creep material behavior is included in an Abaqus/Standard analysis, with the [*DRUCKER PRAGER CREEP](ch04abk35.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Extended Drucker-Prager models," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)
- [*DRUCKER PRAGER HARDENING](ch04abk36.md)
- [*DRUCKER PRAGER CREEP](ch04abk35.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material parameters other than temperature. If this parameter is omitted, it is assumed that the material parameters depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

ECCENTRICITY

This parameter is only for use with SHEAR CRITERION=HYPERBOLIC or SHEAR CRITERION=EXPONENT FORM or if creep material properties are included with SHEAR CRITERION=LINEAR.

It is used to define the flow potential eccentricity, ![](../graphics/key_eqn00222.gif). The eccentricity is a small positive number that defines the rate at which the hyperbolic flow potential approaches its asymptote. The default is ![](../graphics/key_eqn00223.gif) for the exponent model; and if ![](../graphics/key_eqn00625.gif), it is set to ![](../graphics/key_eqn00626.gif) for the hyperbolic model to ensure associated flow (the terms are defined in ["Extended Drucker-Prager models," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)).

SHEAR CRITERION

Set SHEAR CRITERION=LINEAR (default) to define the linear yield criterion. This is required if creep material behavior is included for an Abaqus/Standard analysis. 

Set SHEAR CRITERION=HYPERBOLIC to define the hyperbolic yield criterion. 

Set SHEAR CRITERION=EXPONENT FORM to define the exponent form as a yield criterion.

TEST DATA

This parameter is only for use with SHEAR CRITERION=EXPONENT FORM.

Include this parameter if the material constants for the exponent model are to be computed by Abaqus from triaxial test data at different levels of confining pressure. The [*TRIAXIAL TEST DATA](ch19abk15.md) option must be used for this purpose.

### **Data lines to define a linear Drucker-Prager plasticity model (SHEAR CRITERION=LINEAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.

### **Data lines to define a hyperbolic Drucker-Prager plasticity model (SHEAR CRITERION=HYPERBOLIC): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.

### **Data lines to define a Drucker-Prager plasticity model with the exponent law (SHEAR CRITERION=EXPONENT FORM) and without test data (TEST DATA): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.

### **Data lines to define a Drucker-Prager plasticity model with the exponent law (SHEAR CRITERION=EXPONENT FORM) and with test data (TEST DATA): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.




