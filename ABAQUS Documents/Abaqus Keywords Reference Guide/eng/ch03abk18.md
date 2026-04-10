# *CHARACTERISTIC LENGTH







### *CHARACTERISTIC LENGTHDefine characteristic element length at a material point.

This option is used to define the characteristic element length to be used by Abaqus for the regularization of models that exhibit strain softening or to be passed to user subroutines that are called at the material point. If used, it must appear within a [*MATERIAL](ch13abk08.md) definition (["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)). If this option is not specified, Abaqus computes the characteristic element length using the geometric mean–based definition.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **Reference:**

- ["VUCHARLENGTH," Section 1.2.11 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpucharlength)

### **Optional parameter: **

DEFINITION

Set DEFINITION=GEOMETRIC MEAN (default) to use the geometric mean–based definition of characteristic element length.

Set DEFINITION=USER to specify the characteristic element length in user subroutine [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength).

### **Optional parameters for use with DEFINITION=USER: **

COMPONENTS

Set this parameter equal to the number of components of characteristic element length.

PROPERTIES

Set this parameter equal to the number of properties being entered. The properties are available for use in user subroutine [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength).

### **No data lines are needed for DEFINITION=GEOMETRIC MEAN. **

### **Data lines for DEFINITION=USER when the PROPERTIES parameter is specified: **

**First line:**

Repeat this data line as often as necessary to define all material properties.




