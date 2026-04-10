# *ANISOTROPIC HYPERELASTIC







### *ANISOTROPIC HYPERELASTICSpecify anisotropic hyperelastic properties for approximately incompressible materials.

This option is used to define material constants for a general anisotropic hyperelastic material.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Anisotropic hyperelastic behavior," Section 22.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-canisohyperelastic)
- ["UANISOHYPER_STRAIN," Section 1.1.21 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuanisohyperstrn)
- ["UANISOHYPER_INV," Section 1.1.20 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuanisohyperinv)
- ["VUANISOHYPER_STRAIN," Section 1.2.10 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuanisohyperstrn)
- ["VUANISOHYPER_INV," Section 1.2.9 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuanisohyperinv)

### **Optional, mutually exclusive parameters: **

FUNG-ANISOTROPIC

Include this parameter to use the generalized Fung anisotropic strain energy potential.

FUNG-ORTHOTROPIC

Include this parameter to use the generalized Fung orthotropic strain energy potential.

HOLZAPFEL

Include this parameter to use the Holzapfel-Gasser-Ogden strain energy potential.

USER

Include this parameter if the strain energy potential and its derivatives are defined in a user subroutine (user subroutines [`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv) and [`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain) in Abaqus/Standard or [`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv) and [`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain) in Abaqus/Explicit).

### **Required parameters if the USER parameter is included: **

FORMULATION

Set FORMULATION=STRAIN to indicate that the anisotropic hyperelastic energy potential is formulated in terms of the components of the Green strain tensor and is defined by either [`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain) in Abaqus/Standard or [`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain) in Abaqus/Explicit.

Set FORMULATION=INVARIANT to indicate that the anisotropic hyperelastic energy potential is formulated in terms of pseudo-invariants and is defined by either [`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv) in Abaqus/Standard or [`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv) in Abaqus/Explicit.

TYPE

This parameter applies only to Abaqus/Standard analyses.

Set TYPE=INCOMPRESSIBLE to indicate that the anisotropic hyperelastic material defined by [`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv) or [`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain) is incompressible.

Set TYPE=COMPRESSIBLE to indicate that the hyperelastic material defined by [`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv) or [`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain) is compressible.

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the anisotropic hyperelastic material properties. If this parameter is omitted, it is assumed that the material properties are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LOCAL DIRECTIONS

This parameter can only be used in combination with an invariant-based strain energy potential, such as HOLZAPFEL or USER, FORMULATION=INVARIANT. Set this parameter equal to the number of preferred local directions (or fiber directions) in the material. The default is LOCAL DIRECTIONS=0. 

When LOCAL DIRECTIONS=*N*, the definitions of the *N* local direction vectors in the reference configuration are specified using the [*ORIENTATION](ch15abk01.md), LOCAL DIRECTIONS=*M* option, with *M* ≥ *N*. If *M* > *N*, the first *N* directions will be used.

If the HOLZAPFEL strain energy potential is used, at least one local direction must be specified. 

MODULI

This parameter is applicable only when the [*ANISOTROPIC HYPERELASTIC](ch01abk10.md) option is used in conjunction with the [*VISCOELASTIC](ch21abk04.md) option.

Set MODULI=INSTANTANEOUS to indicate that the anisotropic hyperelastic material constants define the instantaneous behavior. This parameter value is not available for frequency domain viscoelasticity in an Abaqus/Standard analysis. This is the only option available if the anisotropic hyperelastic potential is defined in a user subroutine.

Set MODULI=LONG TERM to indicate that the hyperelastic material constants define the long-term behavior. This option is not available when a user subroutine is used to define the anisotropic hyperelastic potential. It is the default for all other anisotropic hyperelastic models.

PROPERTIES

This parameter can be used only if the USER parameter is specified. Set this parameter equal to the number of property values needed as data in user subroutines [`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv) and [`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain) in Abaqus/Standard or [`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv) and [`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain) in Abaqus/Explicit. The default value is 0.

### **Data lines to define the material constants for the FUNG-ANISOTROPIC model: **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than zero):**

Repeat this set of data lines as often as necessary to define the material constants as a function of temperature and other predefined field variables.

### **Data lines to define the material constants for the FUNG-ORTHOTROPIC model: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the material constants as a function of temperature and other predefined field variables.

### **Data lines to define the material constants for the HOLZAPFEL model: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the material constants as a function of temperature and other predefined field variables.

### **Data lines to define the material properties for the USER anisotropic hyperelasticity model: **

**No data lines are needed if the PROPERTIES parameter is omitted or set to 0. Otherwise, first line:**

Repeat this data line as often as necessary to define the material properties.




