# *ITS







### *ITSDefine properties for ITS elements.

This option is used to define the properties for ITS-type elements. The [*DASHPOT](ch04abk08.md), [*FRICTION](ch06abk36.md), and [*SPRING](ch18abk29.md) options must immediately follow this option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Unsupported; similar functionality (with the exception of friction) is available by modeling connectors.

##### **References:**

- ["Rigid surface contact elements," Section 40.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eirselem)
- [*DASHPOT](ch04abk08.md)
- [*FRICTION](ch06abk36.md)
- [*SPRING](ch18abk29.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the ITS-type elements for which properties are being defined.

### **Data line for ITSUNI elements: **

**First (and only) line:**

### **Data line for ITSCYL elements: **

**First (and only) line:**




