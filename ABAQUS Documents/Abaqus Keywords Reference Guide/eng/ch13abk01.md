# *MAGNETIC PERMEABILITY







### *MAGNETIC PERMEABILITYSpecify magnetic permeability.

This option is used to define magnetic permeability for electromagnetic elements in an electromagnetic or a magnetostatic analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Magnetic permeability," Section 26.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmagpermeability)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["Magnetostatic analysis," Section 6.7.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amagnetostatic)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of magnetic permeability. If this parameter is omitted, the magnetic permeability is assumed not to depend on any field variables but may still depend on temperature and frequency. 

The DEPENDENCIES parameter cannot be used with the NONLINEAR parameter.

FREQUENCY

Include this parameter to specify magnetic permeability as a function of frequency. 

The FREQUENCY parameter cannot be used with the NONLINEAR parameter.

NONLINEAR

Include this parameter if the magnetic behavior is nonlinear and available in tabular form (of magnetic flux density versus magnetic field values). No data line is required if this parameter is used. The tabular data for the magnetic behavior, including field variable–dependent nonlinear magnetic properties, must be provided using the [*NONLINEAR BH](ch14abk14.md) option. 

The NONLINEAR parameter cannot be used with the FREQUENCY and DEPENDENCIES parameters. 

TYPE

Set TYPE=ISOTROPIC (default) to define isotropic magnetic permeability. Set TYPE=ORTHOTROPIC to define orthotropic magnetic permeability. Set TYPE=ANISOTROPIC to define fully anisotropic magnetic permeability.

If the NONLINEAR parameter is also used, the TYPE parameter can be set only to ISOTROPIC or ORTHOTROPIC.

### **Data lines to define isotropic magnetic permeability (TYPE=ISOTROPIC) if the FREQUENCY and NONLINEAR parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define isotropic magnetic permeability as a function of temperature and field variables.

### **Data lines to define isotropic magnetic permeability (TYPE=ISOTROPIC) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define isotropic magnetic permeability as a function of frequency, temperature, and field variables.

### **Data lines to define orthotropic magnetic permeability (TYPE=ORTHOTROPIC) if the FREQUENCY and NONLINEAR parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define orthotropic magnetic permeability as a function of temperature and field variables.

### **Data lines to define orthotropic magnetic permeability (TYPE=ORTHOTROPIC) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define orthotropic magnetic permeability as a function of frequency, temperature, and field variables.

### **Data lines to define anisotropic magnetic permeability (TYPE=ANISOTROPIC) if the FREQUENCY and NONLINEAR parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define anisotropic magnetic permeability as a function of temperature and field variables.

### **Data lines to define anisotropic magnetic permeability (TYPE=ANISOTROPIC) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value equal to or greater than one):**

Repeat this set of data lines as often as necessary to define anisotropic magnetic permeability as a function of frequency, temperature, and field variables.

### **There are no data lines associated with this option if the NONLINEAR parameter is used. **




