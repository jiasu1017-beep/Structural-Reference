# *SHEAR FAILURE







### *SHEAR FAILURESpecify a shear failure model and criterion.

This option is used with the Mises or the Johnson-Cook plasticity models to specify shear failure of the material. It must be used in conjunction with the option [*PLASTIC](ch16abk14.md), HARDENING=ISOTROPIC or JOHNSON COOK.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook plasticity," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["Dynamic failure models," Section 23.2.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfailuremodels)
- [*PLASTIC](ch16abk14.md)

### **Optional parameters: **

DEPENDENCIES

This parameter is relevant only for TYPE=TABULAR.

Set this parameter equal to the number of field variable dependencies included in the definition of the equivalent plastic strain at failure, in addition to temperature. If this parameter is omitted, it is assumed that the strain at failure depends on the plastic strain, the plastic strain rate, the dimensionless pressure-deviatoric stress ratio and, possibly, on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

ELEMENT DELETION

Set ELEMENT DELETION=YES (default) to allow element deletion when the failure criterion is met.

Set ELEMENT DELETION=NO to allow the element to take hydrostatic compressive stress only when the failure criterion is met.

TYPE

Set TYPE=JOHNSON COOK to define the Johnson-Cook shear failure criterion. It requires the use of the [*PLASTIC](ch16abk14.md), HARDENING=JOHNSON COOK option.

Set TYPE=TABULAR (default) to define the failure strain in tabular data form. It requires the use of the [*PLASTIC](ch16abk14.md), HARDENING=ISOTROPIC option.

### **Data lines to define the failure strain in tabular form (TYPE=TABULAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of strain at failure on plastic strain, plastic strain rate, stress ratio and, if needed, on temperature and other predefined field variables.

### **Data line to define the Johnson-Cook shear failure criterion (TYPE=JOHNSON COOK): **

**First (and only) line:**




