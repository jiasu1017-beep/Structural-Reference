# *PLASTIC







### *PLASTICSpecify a metal plasticity model.

This option is used to specify the plastic part of the material model for elastic-plastic materials that use the Mises or Hill yield surface.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Models for metals subjected to cyclic loading," Section 23.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chardening)
- ["Johnson-Cook plasticity," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["Permanent set in rubberlike materials," Section 23.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpermanentset)
- ["UHARD," Section 1.1.36 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuhard)
- ["VUHARD," Section 1.2.17 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexphard)

### **Optional parameters: **

HARDENING

Set HARDENING=ISOTROPIC (default) to specify isotropic hardening.

Set HARDENING=KINEMATIC to specify linear kinematic hardening.

Set HARDENING=COMBINED to specify nonlinear isotropic/kinematic hardening.

Set HARDENING=JOHNSON COOK to specify Johnson-Cook hardening.

Set HARDENING=USER to define isotropic hardening in user subroutine [`UHARD`](../sub/sub-link.md#sub-xsl-uhard) in an Abaqus/Standard analysis or user subroutine [`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard) in an Abaqus/Explicit analysis.

SCALESTRESS

This parameter cannot be used with the HARDENING parameter.

Set this parameter equal to the factor by which you want the yield stress to be scaled.

### **Optional parameter for use with HARDENING=ISOTROPIC or HARDENING=COMBINED: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of hardening behavior, in addition to temperature and possibly strain range. If this parameter is omitted, the hardening behavior does not depend on field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Optional parameter for use with HARDENING=ISOTROPIC: **

RATE

Set this parameter equal to the equivalent plastic strain rate, ![](../graphics/key_eqn00543.gif), for which this stress-strain curve applies.

### **Optional parameters for use with HARDENING=COMBINED: **

DATA TYPE

Set DATA TYPE=HALF CYCLE (default) to specify stress versus plastic strain values of the first half-cycle for calibrating the kinematic hardening parameters.

Set DATA TYPE=PARAMETERS to specify the calibrated kinematic hardening material parameters directly.

Set DATA TYPE=STABILIZED to specify stress versus plastic strain values of a stabilized cycle for calibrating the kinematic hardening parameters.

NUMBER BACKSTRESSES

Set this parameter equal to the number of backstresses. The default number of backstresses is 1, and the maximum allowed is 10.

### **Optional parameter for use with HARDENING=USER: **

PROPERTIES

Set this parameter equal to the number of property values needed as data in user subroutine [`UHARD`](../sub/sub-link.md#sub-xsl-uhard) in Abaqus/Standard analyses and user subroutine [`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard) in Abaqus/Explicit analyses. The default is PROPERTIES=0.

### **Data lines for HARDENING=ISOTROPIC or HARDENING=COMBINED with DATA TYPE=HALF CYCLE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of yield stress on plastic strain and, if needed, on temperature and other predefined field variables.

### **Data lines for HARDENING=COMBINED with DATA TYPE=STABILIZED: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of yield stress on plastic strain and, if needed, on strain range, temperature, and other predefined field variables.

### **Data lines for HARDENING=COMBINED with DATA TYPE=PARAMETERS: **

**First line:**

**Subsequent lines (only needed if the number of entries is greater than eight):**

Repeat this set of data lines as often as necessary to define the dependence of yield stress and kinematic hardening parameters ![](../graphics/key_eqn00996.gif) and ![](../graphics/key_eqn00997.gif) on temperature and other predefined field variables.

### **Data lines for HARDENING=KINEMATIC: **

**First line:**

Repeat this data line a maximum of two times to define linear kinematic hardening independent of temperature. Repeat this set of data lines as often as necessary to define a variation of the linear kinematic hardening modulus with respect to temperature.

### **Data line for HARDENING=JOHNSON COOK: **

**First (and only) line:**

### **Data lines for HARDENING=USER with PROPERTIES: **

**First line:**

Repeat this data line as often as necessary to define all hardening properties.




