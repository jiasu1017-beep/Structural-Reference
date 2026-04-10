# *COMBINED TEST DATA







### *COMBINED TEST DATASpecify simultaneously the normalized shear and bulk compliances or relaxation moduli as functions of time.

This option can be used only in conjunction with the [*VISCOELASTIC](ch21abk04.md) option and cannot be used if the [*SHEAR TEST DATA](ch18abk13.md) and [*VOLUMETRIC TEST DATA](ch21abk08.md) options are used.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Time domain viscoelasticity," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- [*VISCOELASTIC](ch21abk04.md)

### **Optional parameters: **

SHRINF

To specify creep test data, set this parameter equal to the value of the long-term, normalized shear compliance ![](../graphics/key_eqn00196.gif).

To specify relaxation test data, set this parameter equal to the value of the long-term, normalized shear modulus ![](../graphics/key_eqn00197.gif). 

The shear compliance and shear modulus are related by ![](../graphics/key_eqn00198.gif). The fitting procedure will use the specified value in the constraint ![](../graphics/key_eqn00199.gif).

VOLINF

To specify creep test data, set this parameter equal to the value of the long-term, normalized volumetric compliance ![](../graphics/key_eqn00200.gif).

To specify relaxation test data, set this parameter equal to the value of the long-term normalized volumetric modulus ![](../graphics/key_eqn00201.gif). The volumetric compliance and volumetric modulus are related by ![](../graphics/key_eqn00202.gif). The fitting procedure will use this value in the constraint ![](../graphics/key_eqn00203.gif).

### **Data lines to specify creep test data: **

**First line:**

Repeat the above data line as often as necessary to give the compliance-time data.

### **Data lines to specify relaxation test data: **

**First line:**

Repeat the above data line as often as necessary to give the modulus-time data.




