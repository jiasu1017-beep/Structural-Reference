# *PIPE-SOIL STIFFNESS







### *PIPE-SOIL STIFFNESSDefine constitutive behavior for pipe-soil interaction elements.

This option is used to define the constitutive behavior for pipe-soil interaction elements. It can be used only in conjunction with the [*PIPE-SOIL INTERACTION](ch16abk11.md) option. Repeat the option as needed to define behavior in the different local directions.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Pipe-soil interaction elements," Section 32.12.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-epipesoil)
- ["Pipe-soil interaction element library," Section 32.12.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-epipesoillibrary)
- ["UMAT," Section 1.1.41 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uumat)
- [*PIPE-SOIL INTERACTION](ch16abk11.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material property values. If this parameter is omitted, it is assumed that the properties are independent of field variables. See “Using the DEPENDENCIES parameters to define field variable dependence” in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata) for more information.

DIRECTION

Set this parameter equal to the direction in the local orientation system for which the behavior is defined. The DIRECTION parameter can be set equal to a label or to a numerical value. Omit the DIRECTION parameter to define an isotropic model. The DIRECTION parameter must be used to define a constitutive model using the ASCE formulae.

Set DIRECTION=AXIAL (or DIRECTION=1) to specify behavior along the first local direction.

Set DIRECTION=VERTICAL (or DIRECTION=2) to specify behavior along the second local direction.

Set DIRECTION=HORIZONTAL (or DIRECTION=3) to specify behavior along the third local direction. 

TYPE

Set TYPE=LINEAR (default) to define a linear constitutive model.

Set TYPE=NONLINEAR to define a nonlinear constitutive model.

Set TYPE=CLAY to define a constitutive model using the ASCE formulae for clay. This parameter must be used in conjunction with the DIRECTION parameter.

Set TYPE=SAND to define a constitutive model using the ASCE formulae for sand. This parameter must be used in conjunction with the DIRECTION parameter.

Set TYPE=USER to indicate the constitutive behavior is defined in user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat).

### **The following optional parameters can be used only in combination with TYPE=USER: **

PROPERTIES

Set this parameter equal to the number of property values needed as data in user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat). The default is PROPERTIES=0.

VARIABLES

Set this parameter equal to the number of solution-dependent variables that must be stored for the material calculations in user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat). The default is VARIABLES=1.

### **Data lines to define linear constitutive behavior (TYPE=LINEAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the stiffness as a function of temperature and other predefined field variables.

### **Data lines to define nonlinear constitutive behavior (TYPE=NONLINEAR): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the force per unit length as a function of relative displacement, temperature, and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for sand in the axial direction (TYPE=SAND, DIRECTION=AXIAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for clay in the axial direction (TYPE=CLAY, DIRECTION=AXIAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for sand in the vertical direction (TYPE=SAND, DIRECTION=VERTICAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for clay in the vertical direction (TYPE=CLAY, DIRECTION=VERTICAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for sand in the horizontal direction (TYPE=SAND, DIRECTION=HORIZONTAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines to define constitutive behavior using the ASCE formula for clay in the horizontal direction (TYPE=CLAY, DIRECTION=HORIZONTAL): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define parameters for the ASCE formulae as a function of temperature and other predefined field variables.

### **Data lines if the constitutive behavior is defined in user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat) (TYPE=USER): **

**First line:**

Repeat this data line as often as necessary to define properties required in [`UMAT`](../sub/sub-link.md#sub-xsl-umat). Enter eight values per line.




