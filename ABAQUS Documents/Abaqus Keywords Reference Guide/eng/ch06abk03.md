# *FAIL STRESS







### *FAIL STRESSDefine parameters for stress-based failure measures.

This option is used to define the stress limits for stress-based failure measures. It can be used only in conjunction with the [*ELASTIC](ch05abk03.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Plane stress orthotropic failure measures," Section 22.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfailuremeasures)
- [*ELASTIC](ch05abk03.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the failure criteria, in addition to temperature. If this parameter is omitted, it is assumed that the failure criteria depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define stress-based failure criteria: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a nonzero value):**

Repeat this set of data lines as often as necessary to define the failure criterion as a function of temperature and other predefined field variables.




