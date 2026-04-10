# *VISCOUS







### *VISCOUSSpecify viscous material properties for the two-layer viscoplastic model.

This option is used to define the viscous properties for the two-layer viscoplastic material model. It must be used in conjunction with the [*ELASTIC](ch05abk03.md) and [*PLASTIC](ch16abk14.md) options.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Two-layer viscoplasticity," Section 23.2.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cviscous)
- [*ELASTIC](ch05abk03.md)
- [*PLASTIC](ch16abk14.md)
- [*POTENTIAL](ch16abk24.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material properties, in addition to temperature. If this parameter is omitted, it is assumed that the material properties depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=STRAIN (default) to choose a strain-hardening power law.

 Set LAW=TIME to choose a time-hardening power law.

 Set LAW=USER to input the creep law using user subroutine [`CREEP`](../sub/sub-link.md#sub-xsl-creep).

 Set LAW=ANAND to choose an Anand law.

 Set LAW=DARVEAUX to choose a Darveaux law.

 Set LAW=DOUBLE POWER to choose a double power law.

TIME

This parameter is relevant only when LAW=TIME.

Set TIME=CREEP to use creep time in the time-hardening relation.

Set TIME=TOTAL (default) to use total time in the time-hardening relation.

### **Data lines for LAW=TIME or LAW=STRAIN: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the viscous constants on temperature and other predefined field variable.

### **Data lines for LAW=USER: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than seven):**

Repeat this set of data lines as often as necessary to define the dependence of the viscous constants on temperature and other predefined field variables.

### **Data lines for LAW=ANAND: **

**First line:**

**Second line:**

### **Data lines for LAW=DARVEAUX: **

**First line:**

### **Data lines for LAW=DOUBLE POWER: **

**First line:**




