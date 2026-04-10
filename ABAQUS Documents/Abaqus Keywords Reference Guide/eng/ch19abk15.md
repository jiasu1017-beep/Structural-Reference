# *TRIAXIAL TEST DATA







### *TRIAXIAL TEST DATAProvide triaxial test data.

This option is required if some or all of the material parameters that define the exponent form of the [*DRUCKER PRAGER](ch04abk34.md) option are to be calibrated from triaxial test data. This option can be used only as a suboption of the [*DRUCKER PRAGER](ch04abk34.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Extended Drucker-Prager models," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)

### **Optional parameters: **

A

Set this parameter equal to the value of the material constant *a* if it is known and is held fixed at the input value. Omit the parameter and its value if *a* is to be obtained from the calibration.

B

Set this parameter equal to the value of the material constant *b* if it is known and is held fixed at the input value. Omit the parameter and its value if *b* is to be obtained from the calibration.

PT

Set this parameter equal to the value of the material constant ![](../graphics/key_eqn01112.gif) if it is known and is held fixed at the input value. Omit the parameter and its value if ![](../graphics/key_eqn01112.gif) is to be obtained from the calibration.

### **Data lines to specify triaxial test data: **

**First line:**

Repeat this data line as often as necessary to give the yield stress at different levels of confining stress.




