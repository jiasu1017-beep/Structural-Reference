# *ORNL







### *ORNLSpecify constitutive model developed by Oak Ridge National Laboratory.

This option is used to provide plasticity and creep calculations for type 304 and 316 stainless steel according to the specification in Nuclear Standard NEF 9–5 T, “Guidelines and Procedures for Design of Class I Elevated Temperature Nuclear System Components.” It can be used only with the [*PLASTIC](ch16abk14.md) option and/or the [*CREEP](ch03abk85.md), LAW=STRAIN option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["ORNL -- Oak Ridge National Laboratory constitutive model," Section 23.2.12 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cornl)

### **Optional parameters: **

A

Set this parameter equal to the saturation rates for kinematic shift caused by creep strain, as defined by Equation (15) of Section 4.3.3–3 of the Nuclear Standard. The default value is 0.3, as per that section of the Standard. Set A=0.0 to use the 1986 revision of the Standard.

H

Set this parameter equal to the rate of kinematic shift with respect to creep strain [Equation (7) of Section 4.3.2–1 of the Nuclear Standard]. Set H=0.0 to use the 1986 revision of the Standard. If this parameter is omitted, the value of *H* is determined according to Section 4.3.3–3 of the 1981 revision of the Standard.

MATERIAL

Set MATERIAL=SS to use the hardening law appropriate to either type 304 or type 316 stainless steel. This is the only option presently available and, thus, the default.

RESET

Include this parameter to invoke the optional ![](../graphics/key_eqn00080.gif) reset procedure described in Section 4.3.5 of the Nuclear Standard. If this parameter is omitted, the ![](../graphics/key_eqn00080.gif) reset procedure is not used.

**There are no data lines associated with this option.**



