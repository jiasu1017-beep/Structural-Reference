# *VISCOSITY







### *VISCOSITYSpecify material shear viscosity.

This option is used to specify the shear viscosity of the material. When used in Abaqus/Explicit, it must be used in conjunction with the [*EOS](ch05abk27.md) option.

**Products: **Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Viscosity," Section 26.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cviscosity)
- ["Equation of state," Section 25.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ceos)
- ["VUVISCOSITY," Section 1.2.24 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuviscosity)

- [*EOS](ch05abk27.md)
- [*TRS](ch19abk16.md)

### **Optional parameters: **

DEFINITION

Use this parameter to choose the shear viscosity of the material. 

Set DEFINITION=CARREAU-YASUDA to define the Carreau-Yasuda viscous shear behavior.

Set DEFINITION=CROSS to define the Cross viscous shear behavior.

Set DEFINITION=ELLIS-METER to define the Ellis-Meter viscous shear behavior.

Set DEFINITION=HERSCHEL-BULKLEY to define the Herschel-Bulkley viscous shear behavior.

Set DEFINITION=NEWTONIAN (default) to define Newtonian (linear) viscous shear behavior.

Set DEFINITION=POWELL-EYRING to define the Powell-Eyring viscous shear behavior.

Set DEFINITION=POWER LAW to define the power law viscous shear behavior.

Set DEFINITION=TABULAR to define the non-Newtonian viscous shear behavior in tabular form.

Set DEFINITION=USER (Abaqus/Explicit only) to define the viscous shear behavior in user subroutine [`VUVISCOSITY`](../sub/sub-link.md#sub-xsl-vuviscosity). 

DEPENDENCIES

This parameter applies only to Abaqus/Explicit analyses. 

Set this parameter equal to the number of field variable dependencies included in the definition of the viscosity, in addition to temperature. If this parameter is omitted, it is assumed that the viscosity depends only on temperature. 

PROPERTIES

This parameter can be used only if DEFINITION=USER is specified. 

Set this parameter equal to the number of property values needed as data in user subroutine [`VUVISCOSITY`](../sub/sub-link.md#sub-xsl-vuviscosity). The default value is 0.

### **Data lines to define the Carreau-Yasuda viscous shear behavior (DEFINITION=CARREAU-YASUDA): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the coefficients of the Carreau-Yasuda viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define the Cross viscous shear behavior (DEFINITION=CROSS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the coefficients of the Cross viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define the Ellis-Meter viscous shear behavior (DEFINITION=ELLIS-METER): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the coefficients of the Ellis-Meter viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define the Herschel-Bulkley viscous shear behavior (DEFINITION=HERSCHEL-BULKLEY): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the coefficients of the Herschel-Bulkley viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define Newtonian viscous shear behavior (DEFINITION=NEWTONIAN): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the viscosity as a function of temperature and other predefined field variables.

### **Data lines to define the Powell-Eyring viscous shear behavior (DEFINITION=POWELL-EYRING): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the coefficients of the Powell-Eyring viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define the power law viscous shear behavior (DEFINITION=POWER LAW): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the coefficients of the power law viscosity model as a function of temperature and other predefined field variables.

### **Data lines to define the viscous shear behavior in tabular form (DEFINITION=TABULAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the viscosity as a function of effective shear strain rate, temperature, and other predefined field variables.

### **Data lines to define the material properties for the user-defined viscosity model (DEFINITION=USER): **

**No data lines are needed if the PROPERTIES parameter is omitted or set to 0. Otherwise, first line:**

Repeat this data line as often as necessary to define the material properties.




