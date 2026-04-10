# *CONCRETE COMPRESSION HARDENING







### *CONCRETE COMPRESSION HARDENINGDefine hardening in compression for the concrete damaged plasticity model.

This option is used to define the compression hardening data for the concrete damaged plasticity material model. It must be used in conjunction with the [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md) and [*CONCRETE TENSION STIFFENING](ch03abk33.md) options. In addition, the [*CONCRETE TENSION DAMAGE](ch03abk32.md) and/or [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md) options can be used to specify tensile and/or compressive stiffness degradation damage.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete damaged plasticity," Section 23.6.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the compressive yield stress, in addition to temperature. If this parameter is omitted, the compressive yield stress depends only on the inelastic strain, the strain rate, and, possibly, on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define compressive hardening: **

**First line:**

The first point at each value of temperature must have a crushing strain of 0.0 and gives the initial yield stress value, ![](../graphics/key_eqn00220.gif).

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the compressive yield stress on crushing strain, crushing strain rate, and other predefined field variables.




