# *ELECTRICAL CONDUCTIVITY







### *ELECTRICAL CONDUCTIVITYSpecify electrical conductivity.

This option is used to define electrical conductivity for coupled thermal-electrical and coupled thermal-electrical-structural elements in coupled thermal-electrical and coupled thermal-electrical-structural analyses. This option is also used to define electrical conductivity for electromagnetic elements in eddy current analyses.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Electrical conductivity," Section 26.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-celectricconduct)
- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)
- ["Fully coupled thermal-electrical-structural analysis," Section 6.7.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of electrical conductivity. If this parameter is omitted, the electrical conductivity is assumed not to depend on any field variables but may still depend on temperature and frequency. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

FREQUENCY

Include this parameter to specify electrical conductivity as a function of frequency in an eddy current analysis. 

TYPE

Set TYPE=ISO (default) to define isotropic electrical conductivity. Set TYPE=ORTHO to define orthotropic electrical conductivity. Set TYPE=ANISO to define fully anisotropic electrical conductivity.

### **Data lines to define isotropic electrical conductivity (TYPE=ISO) if the FREQUENCY parameter is omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define isotropic electrical conductivity as a function of temperature and field variables.

### **Data lines to define isotropic electrical conductivity (TYPE=ISO) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define isotropic electrical conductivity as a function of frequency, temperature, and field variables.

### **Data lines to define orthotropic electrical conductivity (TYPE=ORTHO) if the FREQUENCY parameter is omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define orthotropic electrical conductivity as a function of temperature and field variables.

### **Data lines to define orthotropic electrical conductivity (TYPE=ORTHO) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define orthotropic electrical conductivity as a function of frequency, temperature, and field variables.

### **Data lines to define anisotropic electrical conductivity (TYPE=ANISO) if the FREQUENCY parameter is omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define anisotropic electrical conductivity as a function of temperature and field variables.

### **Data lines to define anisotropic electrical conductivity (TYPE=ANISO) if the FREQUENCY parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value equal to or greater than one):**

Repeat this set of data lines as often as necessary to define anisotropic electrical conductivity as a function of frequency, temperature, and field variables.




