# *UNIAXIAL







### *UNIAXIALCharacterize fabric materials through loading and unloading test data.

This option is used to indicate the start of shear or uniaxial test data along a particular direction to define the behavior of a fabric material. It must be used in conjunction with the [*FABRIC](ch06abk01.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Fabric material behavior," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- [*FABRIC](ch06abk01.md)
- [*LOADING DATA](ch12abk03.md)
- [*UNLOADING DATA](ch20abk05.md)

### **Required parameter: **

COMPONENT

Set COMPONENT=1 to define uniaxial behavior of fabric fibers in the “fill” direction.

Set COMPONENT=2 to define uniaxial behavior of fabric fibers in the “warp” direction.

Set COMPONENT=SHEAR to define shear response of the fabric.

**There are no data lines associated with this option.**



