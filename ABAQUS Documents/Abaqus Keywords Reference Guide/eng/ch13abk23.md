# *MOHR COULOMB







### *MOHR COULOMBSpecify the Mohr-Coulomb plasticity model.

This option is used to define the yield surface and flow potential parameters for elastic-plastic materials that use the Mohr-Coulomb plasticity model. It must be used in conjunction with the [*MOHR COULOMB HARDENING](ch13abk24.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Mohr-Coulomb plasticity," Section 23.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB HARDENING](ch13abk24.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material parameters other than temperature. If this parameter is omitted, it is assumed that the material properties are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

DEVIATORIC ECCENTRICITY

Set this parameter equal to the flow potential eccentricity in the deviatoric plane, *e*. This feature allows the shape of flow potential in the deviatoric stress space to be controlled independently of the angle of friction. If this parameter is omitted, the deviatoric eccentricity is calculated by default as ![](../graphics/key_eqn00903.gif), where ![](../graphics/key_eqn00878.gif) is the Mohr-Coulomb angle of friction defined on the data lines. The range of values *e* can have is ![](../graphics/key_eqn00904.gif).

ECCENTRICITY

Set this parameter equal to the flow potential eccentricity in the meridional plane, ![](../graphics/key_eqn00222.gif). The meridional eccentricity is a small positive number that defines the rate at which the flow potential approaches its asymptote. The default is ![](../graphics/key_eqn00223.gif).

### **Data lines to define a Mohr-Coulomb plasticity model: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.




