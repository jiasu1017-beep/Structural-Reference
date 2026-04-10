# *POTENTIAL







### *POTENTIALDefine an anisotropic yield/creep model.

This option is used to define stress ratios for anisotropic yield and creep behavior. It can be used only in conjunction with material models defined by the [*CREEP](ch03abk85.md) option, the [*PLASTIC](ch16abk14.md) option (HARDENING=ISOTROPIC, KINEMATIC, or COMBINED; the [*POTENTIAL](ch16abk24.md) option can be used in conjunction with COMBINED hardening only in Abaqus/Explicit), and/or the [*VISCOUS](ch21abk06.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Models for metals subjected to cyclic loading," Section 23.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chardening)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["Anisotropic yield/creep," Section 23.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-canisoyield)
- ["Two-layer viscoplasticity," Section 23.2.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cviscous)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of ![](../graphics/key_eqn01009.gif) in addition to temperature. If this parameter is omitted, it is assumed that the anisotropy ratios are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines used to define stress ratios: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the dependence of ![](../graphics/key_eqn01009.gif) on temperature and other field variables.




