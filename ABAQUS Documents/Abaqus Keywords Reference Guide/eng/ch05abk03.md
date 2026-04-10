# *ELASTIC







### *ELASTICSpecify elastic material properties.

This option is used to define linear elastic moduli. In an Abaqus/Standard analysis spatially varying isotropic, orthotropic (including engineering constants and lamina), or anisotropic linear elastic moduli can be defined for solid continuum elements using a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Linear elastic behavior," Section 22.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-clinearelastic)

### **Optional parameters: **

COMPRESSION FACTOR

This parameter is meaningful only for uncoupled traction-separation elastic behavior. 

Set this parameter equal to the factor by which the elastic modulus, ![](../graphics/key_eqn00641.gif), must be scaled in compression. The use of a factor that is different from 1.0 results in different elastic moduli in tension and compression.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the moduli. If this parameter is omitted, it is assumed that the moduli are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

This parameter is not relevant in an Abaqus/Standard analysis if spatially varying elastic moduli are defined using a distribution. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions).

MODULI

This parameter is applicable only when the [*ELASTIC](ch05abk03.md) option is used in conjunction with the [*VISCOELASTIC](ch21abk04.md) option.

Set MODULI=INSTANTANEOUS to indicate that the elastic material constants define the instantaneous behavior. This parameter value is not available for frequency domain viscoelasticity in an Abaqus/Standard analysis.

Set MODULI=LONG TERM (default) to indicate that the elastic material constants define the long-term behavior.

TYPE

Set TYPE=ANISOTROPIC to define fully anisotropic behavior.

Set TYPE=COUPLED TRACTION to define coupled traction behavior for cohesive elements.

Set TYPE=ENGINEERING CONSTANTS to define orthotropic behavior by giving the “engineering constants” (the generalized Young's moduli, the Poisson's ratios, and the shear moduli in the principal directions).

Set TYPE=ISOTROPIC (default) to define isotropic behavior.

Set TYPE=LAMINA to define an orthotropic material in plane stress.

Set TYPE=ORTHOTROPIC to define orthotropic behavior by giving the elastic stiffness matrix directly. 

Set TYPE=SHEAR to define the (isotropic) shear elastic modulus. This parameter setting is applicable only in conjunction with the [*EOS](ch05abk27.md) option in Abaqus/Explicit.

Set TYPE=SHORT FIBER to define laminate material properties for each layer in each shell element. This parameter setting is applicable only when using Abaqus/Standard in conjunction with the **abaqus moldflow** execution procedure. Any data lines given will be ignored. Material properties will be read from the ASCII neutral file identified as *jobid*`.shf`. See ["Translating Moldflow data to Abaqus input files," Section 3.2.37 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dmflabaproc) for more information.

Set TYPE=TRACTION to define orthotropic shear behavior for warping elements or uncoupled traction behavior for cohesive elements.

 When using a distribution to define elastic moduli, the TYPE parameter must be used to indicate the level of anisotropy in the elastic behavior. The level of anisotropy must be consistent with that defined in the distribution. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions).

### **Data lines to define fully anisotropic elasticity directly (TYPE=ANISOTROPIC): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define coupled traction separation behavior for cohesive elements (TYPE=COUPLED TRACTION): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic elasticity with moduli (TYPE=ENGINEERING CONSTANTS): **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define isotropic elasticity (TYPE=ISOTROPIC): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic elasticity in plane stress (TYPE=LAMINA): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic elasticity directly (TYPE=ORTHOTROPIC): **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define isotropic elastic shear behavior (TYPE=SHEAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the elastic shear modulus as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic shear behavior for warping elements or uncoupled traction behavior for cohesive elements (TYPE=TRACTION): **

**First line (only line for defining orthotropic shear behavior for warping elements; in this case the data cannot be defined as functions of temperature and/or field variables):**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four; relevant only for defining uncoupled traction behavior of cohesive elements):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data line to define spatially varying elastic behavior for solid continuum elements in an Abaqus/Standard analysis using a distribution. (Distributions are supported for TYPE=ISOTROPIC, TYPE=ENGINEERING CONSTANTS, TYPE=LAMINA, TYPE=ORTHOTROPIC, and TYPE=ANISOTROPIC): **

**First line:**




