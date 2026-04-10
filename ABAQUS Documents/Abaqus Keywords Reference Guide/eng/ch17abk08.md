# *RATE DEPENDENT







### *RATE DEPENDENTDefine a rate-dependent viscoplastic model.

This option can be used only as a suboption of the [*PLASTIC](ch16abk14.md), HARDENING=ISOTROPIC option; the [*PLASTIC](ch16abk14.md), HARDENING=JOHNSON COOK option; the [*DRUCKER PRAGER HARDENING](ch04abk36.md) option; or the [*CRUSHABLE FOAM HARDENING](ch03abk88.md) option to introduce strain rate dependence in the material models.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Rate-dependent yield," Section 23.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedependent)
- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook plasticity," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["Extended Drucker-Prager models," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)
- ["Crushable foam plasticity models," Section 23.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccrushfoam)

### **Optional parameters: **

DEPENDENCIES

In an Abaqus/Explicit analysis this parameter is relevant only for TYPE=POWER LAW or TYPE=YIELD RATIO.

Set this parameter equal to the number of field variable dependencies in the definition of material parameters, in addition to temperature. If this parameter is omitted, it is assumed that the rate-dependent material behavior depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=POWER LAW (default) to specify the Cowper-Symonds overstress power law.

Set TYPE=JOHNSON COOK to specify Johnson-Cook rate dependence (this option cannot be used with the crushable foam plasticity model).

Set TYPE=YIELD RATIO to enter yield stress ratios. 

If this option is used in conjunction with the [*CRUSHABLE FOAM](ch03abk87.md) option, the static hardening relation must be defined on the [*CRUSHABLE FOAM HARDENING](ch03abk88.md) option.

### **Data lines to define the overstress power law parameters (TYPE=POWER LAW): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other field variables.

### **Data line to define the Johnson-Cook rate parameters (TYPE=JOHNSON COOK): **

**First (and only) line:**

### **Data lines to define yield stress ratios (TYPE=YIELD RATIO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the yield stress ratio on equivalent plastic strain and, if needed, on temperature and other predefined field variables.




