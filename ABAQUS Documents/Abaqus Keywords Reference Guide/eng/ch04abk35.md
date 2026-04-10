# *DRUCKER PRAGER CREEP







### *DRUCKER PRAGER CREEPSpecify a Drucker-Prager creep law and material properties.

This option is used to define a Drucker-Prager creep model and material properties. Creep behavior defined by this option is active only during [*SOILS](ch18abk21.md), CONSOLIDATION; [*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md); and [*VISCO](ch21abk03.md) procedures. It must be used in conjunction with the [*DRUCKER PRAGER](ch04abk34.md) and [*DRUCKER PRAGER HARDENING](ch04abk36.md) options. The data entered must be consistent with the TYPE parameter used on the [*DRUCKER PRAGER HARDENING](ch04abk36.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Extended Drucker-Prager models," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)
- [*DRUCKER PRAGER](ch04abk34.md)
- [*DRUCKER PRAGER HARDENING](ch04abk36.md)
- ["CREEP," Section 1.1.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ucreep)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the creep constants, in addition to temperature. If this parameter is omitted, it is assumed that the creep constants depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=STRAIN (default) to choose a strain-hardening power law.

Set LAW=TIME to choose a time-hardening power law.

Set LAW=SINGHM to choose a Singh-Mitchell type law.

Set LAW=USER to input the creep law using user subroutine [`CREEP`](../sub/sub-link.md#sub-xsl-creep).

TIME

This parameter is relevant only when LAW=TIME or LAW=SINGHM is used.

Set TIME=CREEP to use creep time.

Set TIME=TOTAL (default) to use total time.

### **Data lines for LAW=TIME or LAW=STRAIN: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the creep constants on temperature and other predefined field variables.

### **Data lines for LAW=SINGHM: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the creep constants on temperature and other predefined field variables.




