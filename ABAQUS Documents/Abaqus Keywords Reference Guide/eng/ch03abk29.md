# *CONCRETE COMPRESSION DAMAGE







### *CONCRETE COMPRESSION DAMAGEDefine compression damage properties for the concrete damaged plasticity model.

This option is used to define compression damage (or stiffness degradation) properties for the concrete damaged plasticity material model. The [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md) option must be used in conjunction with the [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md), [*CONCRETE TENSION STIFFENING](ch03abk33.md), and [*CONCRETE COMPRESSION HARDENING](ch03abk30.md) options. In addition, the [*CONCRETE TENSION DAMAGE](ch03abk32.md) option can be used to specify tensile stiffness degradation damage.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete damaged plasticity," Section 23.6.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the compression damage, in addition to temperature. If this parameter is omitted, it is assumed that the compression damage behavior depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TENSION RECOVERY

This parameter is used to define the stiffness recovery factor ![](../graphics/key_eqn00211.gif), which determines the amount of tension stiffness that is recovered as the loading changes from compression to tension. If ![](../graphics/key_eqn00212.gif), the material fully recovers the tensile stiffness; if ![](../graphics/key_eqn00213.gif), there is no stiffness recovery. Intermediate values of ![](../graphics/key_eqn00211.gif) ![](../graphics/key_eqn00214.gif) result in partial recovery of the tensile stiffness. The default value is 0.0.

### **Data lines to define compression damage: **

**First line:**

The first point at each value of temperature must have a crushing strain of 0.0 and a compressive damage value of 0.0.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the compressive damage behavior on crushing strain, temperature, and other predefined field variables.




