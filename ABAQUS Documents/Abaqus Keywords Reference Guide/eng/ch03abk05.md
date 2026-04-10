# *CAPACITY







### *CAPACITYDefine the molar heat capacity at constant pressure for an ideal gas species.

This option is used to define the molar heat capacity at constant pressure for an ideal gas species.  It can be used only in conjunction with the [*FLUID BEHAVIOR](ch06abk16.md) option.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)
- ["Inflator definition," Section 11.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID BEHAVIOR](ch06abk16.md)
- [*FLUID CAVITY](ch06abk19.md)

### **Required parameter: **

TYPE

Set TYPE=POLYNOMIAL to define the molar heat capacity in the form of a polynomial expression.

Set TYPE=TABULAR to define the molar heat capacity in tabular form.

### **Optional parameter: **

DEPENDENCIES

This parameter is relevant only for TYPE=TABULAR. Set this parameter equal to the number of field variables included in the specification of the molar heat capacity at constant pressure. If this parameter is omitted, the molar heat capacity at constant pressure is assumed not to depend on any field variables but may still depend on temperature. 

### **Data line for TYPE=POLYNOMIAL: **

**First (and only) line:**

### **Data lines for TYPE=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the heat capacity at constant pressure as a function of temperature and other predefined field variables.




