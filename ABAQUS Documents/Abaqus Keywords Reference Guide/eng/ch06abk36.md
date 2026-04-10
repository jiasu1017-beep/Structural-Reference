# *FRICTION







### *FRICTIONSpecify a friction model.

This option is used to introduce friction properties into a mechanical surface interaction model governing the interaction of contact surfaces, a contact pair, or connector elements. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option, the [*CONNECTOR FRICTION](ch03abk43.md) option, or in an Abaqus/Standard analysis with the [*CHANGE FRICTION](ch03abk17.md), the [*GAP](ch07abk01.md), the [*INTERFACE](ch09abk22.md), or the [*ITS](ch09abk23.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model or history data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Part,  Part instance,  Assembly,  Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Mechanical contact properties: overview," Section 37.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["Frictional behavior," Section 37.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afriction)
- ["FRIC," Section 1.1.8 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ufric)
- ["FRIC_COEF," Section 1.1.9 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ufriccoef)
- ["VFRIC," Section 1.2.5 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpfric)
- ["VFRIC_COEF," Section 1.2.6 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpfriccoef)
- ["VFRICTION," Section 1.2.7 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpfriction)
- [*CHANGE FRICTION](ch03abk17.md)
- [*CONNECTOR FRICTION](ch03abk43.md)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*ITS](ch09abk23.md)
- [*SURFACE INTERACTION](ch18abk50.md)

### **Optional, mutually exclusive parameters: **

ELASTIC SLIP

This parameter applies only to Abaqus/Standard analyses.

In a steady-state transport analysis set this parameter equal to the absolute magnitude of the allowable elastic slip velocity (![](../graphics/key_eqn00736.gif)) to be used in the stiffness method for sticking friction. In all other analysis procedures set this parameter equal to the absolute magnitude of the allowable elastic slip (![](../graphics/key_eqn00737.gif)) to be used in the stiffness method for sticking friction. If this parameter is omitted, the elastic slip (or elastic slip velocity) is defined by the SLIP TOLERANCE value.

LAGRANGE

This parameter applies only to Abaqus/Standard analyses and cannot be used when friction is defined for connector elements.

Include this parameter to choose the Lagrange multiplier formulation for friction.

ROUGH

This parameter cannot be used when friction is defined for connector elements.

Include this parameter to specify completely rough (no slipping) friction.

SLIP TOLERANCE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the value of ![](../graphics/key_eqn00738.gif) (defined as the ratio of allowable maximum elastic slip velocity to angular velocity times the diameter of the spinning body in a steady-state transport analysis or as the ratio of allowable maximum elastic slip to characteristic contact surface face dimension in all other analysis procedures). The default is SLIP TOLERANCE=.005.

When friction is defined for connector elements, ![](../graphics/key_eqn00738.gif) is defined (when possible) as the ratio of allowable maximum elastic slip to a characteristic element dimension in the model. In this case the default is SLIP TOLERANCE=.0001.

USER

This parameter cannot be used when friction is defined for connector elements.

In an Abaqus/Standard analysis, set USER=FRIC (default) if the friction model is to be defined in user subroutine [`FRIC`](../sub/sub-link.md#sub-xsl-fric). Set USER=COEFFICIENT if the friction coefficient is to be defined in user subroutine [`FRIC_COEF`](../sub/sub-link.md#sub-xsl-fric_coef).

In an Abaqus/Explicit analysis, set USER=FRIC (default) if the friction model is to be defined in user subroutine [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric). Set USER=FRICTION if the friction model is to be defined in user subroutine [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction). [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric) is applicable to contact pairs, whereas [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction) is applicable to general contact. Set USER=COEFFICIENT if the friction coefficient is to be defined in user subroutine [`VFRIC_COEF`](../sub/sub-link.md#sub-xsl-vfric_coef). [`VFRIC_COEF`](../sub/sub-link.md#sub-xsl-vfric_coef) can be used only with general contact.

### **Optional parameters: **

ANISOTROPIC

This parameter applies only to Abaqus/Standard analyses and cannot be used when friction is defined for connector elements.

Include this parameter if anisotropic friction is being defined.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the friction coefficient in addition to slip rate, contact pressure, and temperature. If this parameter is omitted, it is assumed that the friction coefficients have no dependencies or depend only on slip rate, contact pressure, and temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

DEPVAR

This parameter is valid only if the USER parameter is included.

Set DEPVAR equal to the number of state-dependent variables required for user subroutine [`FRIC`](../sub/sub-link.md#sub-xsl-fric) in an Abaqus/Standard analysis or for user subroutines [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric) and [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction) in an Abaqus/Explicit analysis. The default is DEPVAR=0.

EXPONENTIAL DECAY

Include this parameter to specify separate static and kinetic friction coefficients with a smooth transition zone defined by an exponential curve.

The ANISOTROPIC and TAUMAX parameters cannot be used with this parameter.

PROPERTIES

This parameter is valid only if the USER parameter is included.

Set this parameter equal to the number of property values needed as data to define the friction model in user subroutine [`FRIC`](../sub/sub-link.md#sub-xsl-fric) and [`FRIC_COEF`](../sub/sub-link.md#sub-xsl-fric_coef) in an Abaqus/Standard analysis or in user subroutines [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric), [`VFRIC_COEF`](../sub/sub-link.md#sub-xsl-vfric_coef), and [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction) in an Abaqus/Explicit analysis. The default is PROPERTIES=0.

SHEAR TRACTION SLOPE

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the slope of the curve that defines the shear traction as a function of the elastic slip between the two surfaces. If this parameter is omitted or frictional forces are not present, shear softening will not be activated. This parameter cannot be used in conjunction with user subroutines [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric), [`VFRIC_COEF`](../sub/sub-link.md#sub-xsl-vfric_coef), and [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction).

TAUMAX

Set this parameter equal to the equivalent shear stress limit, ![](../graphics/key_eqn00739.gif); that is, the maximum achievable value of the equivalent shear stress. If no value is given or TAUMAX=0 in an Abaqus/Standard analysis, there is no limit on the equivalent shear stress. A value of zero is not allowed in an Abaqus/Explicit analysis.

TEST DATA

This parameter is valid only if the EXPONENTIAL DECAY parameter is used.

Include this parameter if the exponential decay coefficient, ![](../graphics/key_eqn00740.gif), is to be computed by Abaqus. If this parameter is omitted, the decay coefficient must be given directly on the data line.

### **Data lines to define the coefficient of friction if the USER, ROUGH, EXPONENTIAL DECAY, and ANISOTROPIC parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the friction coefficient as a function of contact pressure, slip rate, average surface temperature, and other predefined field variables.

### **Data lines to define the coefficient of friction if the ANISOTROPIC parameter is used and the USER, ROUGH, and EXPONENTIAL DECAY parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the friction coefficient as a function of contact pressure, slip rate, average surface temperature, and other predefined field variables.

### **Data line to define the static and kinetic friction coefficients if the EXPONENTIAL DECAY parameter is used and the decay coefficient is specified directly: **

**First (and only) line:**

### **Data lines if the EXPONENTIAL DECAY and TEST DATA parameters are used: **

**First line:**

**Second line:**

**Third line (optional):**

### **Data line when the ROUGH parameter is used: **

There are no data lines in this case.

### **Data lines to define the user subroutine properties if the PROPERTIES parameter is used: **

**First line:**

Repeat this data line as often as necessary to completely define all of the properties needed by user subroutines [`FRIC`](../sub/sub-link.md#sub-xsl-fric), [`FRIC_COEF`](../sub/sub-link.md#sub-xsl-fric_coef), [`VFRIC`](../sub/sub-link.md#sub-xsl-vfric), [`VFRIC_COEF`](../sub/sub-link.md#sub-xsl-vfric_coef), and [`VFRICTION`](../sub/sub-link.md#sub-xsl-vfriction) as indicated by the value of PROPERTIES.

### **Data line when the USER parameter is used without the PROPERTIES parameter: **

There are no data lines in this case.




