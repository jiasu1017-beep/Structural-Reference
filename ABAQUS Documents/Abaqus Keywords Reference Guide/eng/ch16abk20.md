# *POROUS ELASTIC







### *POROUS ELASTICSpecify elastic material properties for porous materials.

This option is used to define the elastic parameters for porous materials.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Elastic behavior of porous materials," Section 22.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-celasticporous)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the parameters, in addition to temperature. If this parameter is omitted, it is assumed that the parameters depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

SHEAR

Set SHEAR=G to define the deviatoric behavior with a constant shear modulus *G*. Set SHEAR=POISSON (default) to compute the instantaneous shear modulus from the bulk modulus and Poisson's ratio. The Poisson's ratio should be given on the data lines.

### **Data lines to define the deviatoric behavior with a constant shear modulus *G*: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters ![](../graphics/key_eqn00073.gif), *G*, and ![](../graphics/key_eqn01001.gif) on temperature and field variables.

### **Data lines to define the instantaneous shear modulus from the bulk modulus and Poisson's ratio: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters ![](../graphics/key_eqn00073.gif), ![](../graphics/key_eqn00579.gif), and ![](../graphics/key_eqn01001.gif) on temperature and field variables.




