# *TENSILE FAILURE







### *TENSILE FAILURESpecify a tensile failure model and criterion.

This option is used with the Mises or the Johnson-Cook plasticity models or the equation of state model to specify a tensile failure model and criterion. It must be used in conjunction with the [*PLASTIC](ch16abk14.md), HARDENING=ISOTROPIC option; the [*PLASTIC](ch16abk14.md), HARDENING=JOHNSON COOK option; or the [*EOS](ch05abk27.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Equation of state," Section 25.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ceos)
- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook plasticity," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["Dynamic failure models," Section 23.2.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfailuremodels)
- [*EOS](ch05abk27.md)
- [*PLASTIC](ch16abk14.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the hydrostatic cutoff stress, in addition to temperature. If this parameter is omitted, it is assumed that the hydrostatic cutoff stress is constant or depends only on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

ELEMENT DELETION

Set ELEMENT DELETION=YES (default) to allow element deletion when the failure criterion is met.

Set ELEMENT DELETION=NO to allow BRITTLE/DUCTILE-type failure for the deviatoric and hydrostatic parts of stresses.

### **Required parameters for use with ELEMENT DELETION=NO: **

PRESSURE

Set PRESSURE=BRITTLE to model the case where the pressure stress is required to be compressive when the failure criterion is met.

Set PRESSURE=DUCTILE to model the case where the pressure stress will be limited by the hydrostatic cutoff stress when the failure criterion is met.

SHEAR

Set SHEAR=BRITTLE to model the case where the deviatoric stresses will be set to zero when the failure criterion is met.

Set SHEAR=DUCTILE to model the case where the deviatoric stresses will be unaffected when the failure criterion is met.

### **Data lines to specify a tensile failure model: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of hydrostatic cutoff stress as a function of temperature and other predefined field variables.




