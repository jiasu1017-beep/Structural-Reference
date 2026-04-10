# *CAP CREEP







### *CAP CREEPSpecify a cap creep law and material properties.

This option is used to define a cap creep model and material properties. Creep behavior defined by this option is active only during [*SOILS](ch18abk21.md), CONSOLIDATION; [*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md); and [*VISCO](ch21abk03.md) procedures. It must be used in conjunction with the [*CAP PLASTICITY](ch03abk04.md) and the [*CAP HARDENING](ch03abk03.md) options.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Modified Drucker-Prager/Cap model," Section 23.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP PLASTICITY](ch03abk04.md)
- [*CAP HARDENING](ch03abk03.md)
- ["CREEP," Section 1.1.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ucreep)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the creep constants, in addition to temperature. If this parameter is omitted, it is assumed that the creep constants depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=STRAIN (default) to choose a strain hardening power law.

Set LAW=TIME to choose a time hardening power law. 

Set LAW=SINGHM to choose a Singh-Mitchell type law. 

Set LAW=USER to input the creep law using user subroutine [`CREEP`](../sub/sub-link.md#sub-xsl-creep).

MECHANISM

Set MECHANISM=COHESION (default) to choose the cohesion creep mechanism, which is similar in behavior to Drucker-Prager creep.

Set MECHANISM=CONSOLIDATION to choose the consolidation creep mechanism, which is similar in behavior to the cap zone of plasticity.

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




