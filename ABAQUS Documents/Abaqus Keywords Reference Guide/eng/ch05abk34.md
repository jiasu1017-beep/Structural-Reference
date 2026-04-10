# *EXPANSION







### *EXPANSIONSpecify thermal or field expansion.

This option is used to define thermal expansion or field expansion in Abaqus/Standard for a material or for the behavior of a gasket. In an Abaqus/Standard analysis spatially varying thermal expansion can be defined for solid continuum elements using a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)). In an Abaqus/CFD analysis this option is used to define thermal expansion for computing bouyancy forces.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Thermal expansion," Section 26.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cthermalexpan)
- ["Field expansion," Section 26.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfieldexpansion)
- ["UEXPAN," Section 1.1.30 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuexpan)

### **Optional parameters: **

DEPENDENCIES

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses. 

Set this parameter equal to the number of field variables, in addition to temperature, on which the coefficients depend. If this parameter is omitted, it is assumed that the thermal expansion is constant or depends only on temperature. 

This parameter is not relevant if the USER parameter is included or if in an Abaqus/Standard analysis spatially varying thermal expansion is defined using a distribution (see ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)). 

FIELD

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the predefined field variable number for which field expansion is being defined. 

PORE FLUID

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the thermal expansion of the pore fluid in a porous medium is being defined. The thermal expansion of a fluid must be isotropic, so TYPE=ORTHO and TYPE=ANISO cannot be used if this parameter is included. 

TYPE

Set TYPE=ISO (default) to define isotropic expansion. The only option that is available in an Abaqus/CFD analysis is TYPE=ISO.

Set TYPE=ORTHO to define orthotropic expansion. 

Set TYPE=ANISO to define fully anisotropic expansion in an Abaqus/Standard analysis.

Set TYPE=SHORT FIBER to define laminate material properties for each layer in each shell element. This parameter setting is applicable only when using Abaqus/Standard in conjunction with the **abaqus moldflow** execution procedure. Any data lines will be ignored. Material properties will be read from the ASCII neutral file identified as *jobid*`.shf`. See ["Translating Moldflow data to Abaqus input files," Section 3.2.37 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dmflabaproc) for more information.

In an Abaqus/Standard analysis spatially varying isotropic, orthotropic, or anisotropic expansion can be defined using a distribution. When using a distribution, the TYPE parameter must be used to indicate the level of anisotropy of thermal expansion. The level of anisotropy must be consistent with that defined in the distribution. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions).

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to indicate that user subroutine [`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan) will be used to define increments of thermal strain. The TYPE parameter should be used to indicate the level of anisotropy of thermal expansion. The PORE FLUID parameter can also be used to indicate that the thermal expansion of the pore fluid is being defined.

The DEPENDENCIES and ZERO parameters are not relevant if this parameter is used.

ZERO

If the thermal expansion is temperature- or field-variable-dependent, set this parameter equal to the value of ![](../graphics/key_eqn00086.gif). The default is ZERO=0.

This parameter is not relevant if the USER parameter is included. 

In Abaqus/CFD this parameter should be set equal to the reference temperature used for the Boussinesq approximation of buoyancy forces.

### **Data lines to define isotropic thermal expansion coefficients (TYPE=ISO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the thermal expansion coefficient as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic thermal expansion coefficients (TYPE=ORTHO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the thermal expansion coefficients as functions of temperature and other predefined field variables.

### **Data lines to define anisotropic thermal expansion coefficients (TYPE=ANISO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the thermal expansion coefficients as functions of temperature and other predefined field variables.

### **Data line to define spatially varying thermal expansion in an Abaqus/Standard analysis using a distribution: **

**First (and only) line:**

### **To define thermal expansion by a user subroutine (USER parameter included): **

No data lines are used with this option when the USER parameter is specified. Instead, user subroutine [`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan) must be used to define the thermal expansion.

### **Data lines to define isotropic field expansion coefficients (TYPE=ISO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the field expansion coefficient as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic field expansion coefficients (TYPE=ORTHO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the field expansion coefficients as functions of temperature and other predefined field variables.

### **Data lines to define anisotropic field expansion coefficients (TYPE=ANISO with USER parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the field expansion coefficients as functions of temperature and other predefined field variables.

### **To define field expansion by a user subroutine (USER parameter included): **

No data lines are used with this option when the USER parameter is specified. Instead, user subroutine [`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan) must be used to define the field expansion.




