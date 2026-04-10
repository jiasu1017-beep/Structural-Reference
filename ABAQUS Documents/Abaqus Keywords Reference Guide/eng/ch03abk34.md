# *CONDUCTIVITY







### *CONDUCTIVITYSpecify thermal conductivity.

This option is used to specify a material's thermal conductivity.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Conductivity," Section 26.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconductivity)

### **Optional parameters: **

DEPENDENCIES

 This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses.

Set this parameter equal to the number of field variables included in the definition of conductivity. If this parameter is omitted, it is assumed that the conductivity is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

PORE FLUID

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the conductivity of the pore fluid in a porous medium is being defined. The conductivity of a fluid must be isotropic; therefore, TYPE=ORTHO and TYPE=ANISO cannot be used if this parameter is included.

TYPE

Set TYPE=ISO (default) to define isotropic conductivity. Set TYPE=ORTHO to define orthotropic conductivity. Set TYPE=ANISO to define fully anisotropic conductivity. Abaqus/CFD supports only isotropic conductivity without field-dependent variants.

### **Data lines to define isotropic thermal conductivity (TYPE=ISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the thermal conductivity as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic thermal conductivity (TYPE=ORTHO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the thermal conductivity as a function of temperature and other predefined field variables.

### **Data lines to define anisotropic thermal conductivity (TYPE=ANISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the thermal conductivity as a function of temperature and other predefined field variables.




