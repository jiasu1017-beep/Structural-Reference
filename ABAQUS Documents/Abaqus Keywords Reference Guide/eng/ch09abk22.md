# *INTERFACE







### *INTERFACEDefine properties for contact elements.

This option is used to assign element section properties to ITT-, ISL-, IRS-, and ASI-type contact elements.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module; supported for two-dimensional, three-dimensional, and axisymmetric acoustic interface elements. Contact elements are not supported.

##### **References:**

- ["Acoustic interface elements," Section 32.13.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-einteracoust)
- ["Tube-to-tube contact elements," Section 40.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eitt)
- ["Slide line contact elements," Section 40.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eslidelineelem)
- ["Rigid surface contact elements," Section 40.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eirselem)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the ITT-, ISL-, IRS-, and ASI-type contact elements for which properties are being defined.

### **Optional parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this interface definition. The label given can be used to identify this particular interface definition in user subroutines such as [`GAPCON`](../sub/sub-link.md#sub-xsl-gapcon).

### **Data line for ITT-type elements: **

**First (and only) line:**

### **Data lines for ISL21A and ISL22A elements: **

There are no data lines.

### **Data lines for IRS-type elements for use with axisymmetric elements: **

There are no data lines.

### **Data line for ASI1 elements: **

**First (and only) line:**

### **Data line for ASI-type elements for use with 2D elements: **

**First (and only) line:**

### **Data lines for ASI-type elements for use with axisymmetric elements or 3D elements: **

There are no data lines.




