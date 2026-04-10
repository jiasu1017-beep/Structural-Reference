# *CREEP







### *CREEPDefine a creep law.

This option is used when metal creep behavior is to be included in a material definition. Metal creep behavior defined is active only during [*DIRECT CYCLIC](ch04abk24.md); [*SOILS](ch18abk21.md), CONSOLIDATION; [*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md); [*STEADY STATE TRANSPORT](ch18abk35.md); and [*VISCO](ch21abk03.md) procedures. This option can also be used to define creep behavior in the thickness direction in a gasket; in this case the option is active only during the [*VISCO](ch21abk03.md) procedure.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["Anisotropic yield/creep," Section 23.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-canisoyield)
- ["CREEP," Section 1.1.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ucreep)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the creep constants in addition to temperature. If this parameter is omitted, it is assumed that the creep constants have no dependencies or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=STRAIN (default) to choose a strain-hardening power law.

 Set LAW=TIME to choose a time-hardening power law.

 Set LAW=HYPERB to choose a hyperbolic-sine law.

 Set LAW=USER to input the creep law using user subroutine [`CREEP`](../sub/sub-link.md#sub-xsl-creep).

 Set LAW=ANAND to choose an Anand law.

 Set LAW=DARVEAUX to choose a Darveaux law.

 Set LAW=DOUBLE POWER to choose a double power law.

TIME

This parameter is relevant only when LAW=TIME is used.

Set TIME=CREEP to use creep time in the time-hardening relation.

Set TIME=TOTAL (default) to use total time in the time-hardening relation.

### **Data lines for LAW=TIME or LAW=STRAIN: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the creep constants on temperature and other predefined field variables.

### **Data lines for LAW=HYPERB: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the creep constants on predefined field variables.

### **Data lines for LAW=ANAND: **

**First line:**

**Second line:**

### **Data lines for LAW=DARVEAUX: **

**First line:**

### **Data lines for LAW=DOUBLE POWER: **

**First line:**




