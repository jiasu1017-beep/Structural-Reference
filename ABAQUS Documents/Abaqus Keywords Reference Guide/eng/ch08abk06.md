# *HYPERELASTIC







### *HYPERELASTICSpecify elastic properties for approximately incompressible elastomers.

This option is used to define material constants for a general hyperelastic material.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Hyperelastic behavior of rubberlike materials," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperelastic)
- ["UHYPER," Section 1.1.38 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuhyper)
- [*BIAXIAL TEST DATA](ch02abk09.md)
- [*PLANAR TEST DATA](ch16abk13.md)
- [*UNIAXIAL TEST DATA](ch20abk04.md)
- [*VOLUMETRIC TEST DATA](ch21abk08.md)

### **Optional, mutually exclusive parameters: **

ARRUDA-BOYCE

Include this parameter to use the Arruda-Boyce model, also known as the eight-chain model.

MARLOW

Include this parameter to use the Marlow model.

MOONEY-RIVLIN

Include this parameter to use the Mooney-Rivlin model. This method is equivalent to using the POLYNOMIAL parameter with N=1.

NEO HOOKE

Include this parameter to use the neo-Hookean model. This method is equivalent to using the REDUCED POLYNOMIAL parameter with N=1.

OGDEN

Include this parameter to use the Ogden strain energy potential.

POLYNOMIAL

Include this parameter to use the polynomial strain energy potential. This method is the default method of defining the strain energy potential.

REDUCED POLYNOMIAL

Include this parameter to use the reduced polynomial strain energy potential. This method is equivalent to using the POLYNOMIAL parameter with ![](../graphics/key_eqn00781.gif) for ![](../graphics/key_eqn00782.gif).

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the derivatives of the strain energy potential with respect to the strain invariants are defined in user subroutine [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper).

VAN DER WAALS

Include this parameter to use the Van der Waals model, also known as the Kilian model.

YEOH

Include this parameter to use the Yeoh model. This method is equivalent to using the REDUCED POLYNOMIAL parameter with N=3.

### **Required parameter if the USER parameter is included: **

TYPE

This parameter applies only to Abaqus/Standard analyses.

Set TYPE=INCOMPRESSIBLE to indicate that the hyperelastic material defined by [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) is incompressible.

Set TYPE=COMPRESSIBLE to indicate that the hyperelastic material defined by [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) is compressible.

### **Optional parameters: **

BETA

This parameter can be used only when both the VAN DER WAALS and TEST DATA INPUT parameters are used; it defines the value of ![](../graphics/key_eqn00135.gif) while the other coefficients of the Van der Waals model are fitted from the test data given by the user. If this parameter is omitted, ![](../graphics/key_eqn00135.gif) will be determined from a nonlinear, least-squares fit of the test data. Allowable values of BETA are ![](../graphics/key_eqn00783.gif). It is recommended to set ![](../graphics/key_eqn00135.gif) = 0 if only one type of test data is available.

MODULI

This parameter is applicable only when the [*HYPERELASTIC](ch08abk06.md) option is used in conjunction with the [*VISCOELASTIC](ch21abk04.md) or the [*HYSTERESIS](ch08abk09.md) option.

Set MODULI=INSTANTANEOUS to indicate that the hyperelastic material constants define the instantaneous behavior. This parameter value is not available for frequency domain viscoelasticity in an Abaqus/Standard analysis. This is the only option available if the hyperelastic material is defined in user subroutine [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper).

Set MODULI=LONG TERM to indicate that the hyperelastic material constants define the long-term behavior. This option is not available when user subroutine [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) is used to define the hyperelastic material. It is the default for all other hyperelastic models.

N

This parameter can be used only with the OGDEN, POLYNOMIAL, and REDUCED POLYNOMIAL parameters. Include this parameter to define the order of the strain energy potential. The default is N=1.

If the TEST DATA INPUT parameter is used, the parameter N can take only the values 1 or 2 for the POLYNOMIAL form and up to 6 for the OGDEN and REDUCED POLYNOMIAL forms.

If the TEST DATA INPUT parameter is omitted, the maximum value of N is 6 for either form.

POISSON

Set this parameter equal to the Poisson's ratio, ![](../graphics/key_eqn00579.gif), to account for compressibility. This parameter cannot be used if the material coefficients are specified directly or if volumetric behavior is defined by entering nonzero values for ![](../graphics/key_eqn00784.gif) on the data line or by specifying the [*VOLUMETRIC TEST DATA](ch21abk08.md) option. In addition, this parameter cannot be used for the Marlow model if the nominal lateral strains are specified on the [*UNIAXIAL TEST DATA](ch20abk04.md), [*BIAXIAL TEST DATA](ch02abk09.md), or [*PLANAR TEST DATA](ch16abk13.md) option.

PROPERTIES

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used only if the USER parameter is specified. Set this parameter equal to the number of property values needed as data in user subroutine [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper). The default value is 0.

TEST DATA INPUT

Include this parameter if the material constants are to be computed by Abaqus from data taken from simple tests on a material specimen.

If this parameter is omitted, the material constants must be given directly on the data lines. This parameter is not relevant for the Marlow model, in which case the test data must be specified.

### **To define the material behavior by giving test data: **

Alternative options for specifying test data rather than specifying relevant material constants on the data lines of the [*HYPERELASTIC](ch08abk06.md) option are applicable to all hyperelastic material models except the user-defined model. No data lines are used with the [*HYPERELASTIC](ch08abk06.md) option when the MARLOW or TEST DATA INPUT parameter is specified. In this case the test data are specified with the [*BIAXIAL TEST DATA](ch02abk09.md), [*PLANAR TEST DATA](ch16abk13.md), [*UNIAXIAL TEST DATA](ch20abk04.md), and [*VOLUMETRIC TEST DATA](ch21abk08.md) options.

### **Data lines to define the material constants for the ARRUDA-BOYCE model: **

**First line:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

### **Data lines to define the material constants for the MOONEY-RIVLIN model: **

**First line:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

### **Data lines to define the material constants for the NEO HOOKE model: **

**First line:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

### **Data lines to define the material constants for the OGDEN strain energy potential: **

**First line if N=1:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=2:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=3:**

**Second line if N=3:**

Repeat this pair of data lines as often as necessary to define the material constants as a function of temperature.

**Data lines for higher values of N (up to 6):**

### **Data lines to define the material constants for the POLYNOMIAL strain energy potential: **

**First line if N=1:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=2:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=3:**

**Second line if N=3:**

Repeat this pair of data lines as often as necessary to define the material constants as a function of temperature.

**Data lines for higher values of N (up to 6):**

### **Data lines to define the material constants for the REDUCED POLYNOMIAL strain energy potential: **

**First line if N=1:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=2:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=3:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**Data lines for higher values of N (up to 6):**

### **Data lines to define the material properties for the USER hyperelasticity model: **

**No data lines are needed if the PROPERTIES parameter is omitted or set to 0. Otherwise, first line:**

Repeat this data line as often as necessary to define the material properties.

### **Data lines to define the material constants for the VAN DER WAALS model: **

**First line:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

### **Data lines to define the material constants for the YEOH model: **

**First line:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.




