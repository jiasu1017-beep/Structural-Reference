# *CONCRETE DAMAGED PLASTICITY







### *CONCRETE DAMAGED PLASTICITYDefine flow potential, yield surface, and viscosity parameters for the concrete damaged plasticity model.

This option is used to define flow potential, yield surface, and viscosity parameters for the concrete damaged plasticity material model. The [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md) option must be used in conjunction with the [*CONCRETE TENSION STIFFENING](ch03abk33.md) and the [*CONCRETE COMPRESSION HARDENING](ch03abk30.md) options. In addition, the [*CONCRETE TENSION DAMAGE](ch03abk32.md) and/or the [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md) options can be used to specify tensile and/or compressive stiffness degradation damage.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete damaged plasticity," Section 23.6.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material parameters other than temperature. If this parameter is omitted, it is assumed that the material parameters depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define concrete damaged plasticity flow potential, yield surface, and viscosity parameters: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.




