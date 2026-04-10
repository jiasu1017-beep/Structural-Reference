# *ASYMMETRIC-AXISYMMETRIC







### *ASYMMETRIC-AXISYMMETRICDefine areas of integration for contact elements used with CAXA*n* or SAXA*n* elements.

This option is used to allow Abaqus/Standard to calculate appropriate areas of integration for ISL- and IRS-type contact elements used in conjunction with CAXA*n* or SAXA*n* elements. The [*ASYMMETRIC-AXISYMMETRIC](ch01abk15.md) option must be used in conjunction with the [*INTERFACE](ch09abk22.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

##### **References:**

- ["Contact interaction analysis: overview," Section 36.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactoverview)
- ["Contact modeling if asymmetric-axisymmetric elements are present," Section 36.3.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactasymmaxisymm)
- [*INTERFACE](ch09abk22.md)

### **Required parameters: **

ANGLE

Set this parameter equal to the angular position (measured in degrees) of the circumferential plane in which the contact elements exists. Valid values are ![](../graphics/key_eqn00075.gif) = 0, 180 for *n* = 1; ![](../graphics/key_eqn00075.gif) = 0, 90, 180 for *n* = 2; ![](../graphics/key_eqn00075.gif) = 0, 60, 120, 180 for *n* = 3; and ![](../graphics/key_eqn00075.gif) = 0, 45, 90, 135, 180 for *n* = 4. Abaqus/Standard does not model contact correctly on other circumferential planes. 

MODE

Set this parameter equal to the number of Fourier modes used with the CAXA*n* or SAXA*n* elements that share nodes with the contact elements.

**There are no data lines associated with this option.**



