# *BUCKLING REDUCTION FACTORS







### *BUCKLING REDUCTION FACTORSDefine buckling reduction factors for buckling strut response of frame elements with PIPE sections.

This option is used to define two coefficients used in the ISO equation, which predicts ![](../graphics/key_eqn00138.gif), the axial load at which the response switches to buckling only, for frame elements with buckling strut response. For a nondefault buckling envelope the [*BUCKLING REDUCTION FACTORS](ch02abk19.md) option can be used only in conjunction with both the [*FRAME SECTION](ch06abk34.md), SECTION=PIPE, YIELD STRESS=![](../graphics/key_eqn00128.gif) option and the [*BUCKLING ENVELOPE](ch02abk17.md) option. For the default buckling envelope it can be used only in conjunction with the [*FRAME SECTION](ch06abk34.md), BUCKLING, SECTION=PIPE, YIELD STRESS=![](../graphics/key_eqn00128.gif) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance,  Model  

##### **References:**

- ["Frame elements," Section 29.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eframe)
- ["Frame section behavior," Section 29.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingframesection)
- ["Buckling strut response for frame elements," Section 3.9.3 of the Abaqus Theory Guide](../stm/stm-link.md#stm-elm-strut)

### **Optional parameters: **

AXIS1

Include this parameter to define the method for calculating the buckling reduction factor ![](../graphics/key_eqn00139.gif) for bending about the first cross-section direction.

Set AXIS1=TYPE1 (default) to set ![](../graphics/key_eqn00139.gif) to the constant value of ![](../graphics/key_eqn00140.gif).

Set AXIS1=TYPE2 for members with no distributed transverse loading. Then ![](../graphics/key_eqn00139.gif)=max![](../graphics/key_eqn00141.gif), where ![](../graphics/key_eqn00142.gif) is the ratio of smaller to larger moments about the first cross-section axis at the element ends.

Set AXIS1=TYPE3 for members with distributed transverse loading. Then ![](../graphics/key_eqn00139.gif)=min![](../graphics/key_eqn00143.gif), where ![](../graphics/key_eqn00144.gif) is the compressive axial stress and ![](../graphics/key_eqn00145.gif) is the Euler buckling stress corresponding to the first cross-section direction.

AXIS2

Include this parameter to define the method for calculating the buckling reduction factor ![](../graphics/key_eqn00146.gif) for bending about the second cross-section direction.

Set AXIS2=TYPE1 (default) to set ![](../graphics/key_eqn00146.gif) to the constant value of ![](../graphics/key_eqn00140.gif).

Set AXIS2=TYPE2 for members with no distributed transverse loading. Then ![](../graphics/key_eqn00146.gif)=max![](../graphics/key_eqn00141.gif), where ![](../graphics/key_eqn00142.gif) is the ratio of smaller to larger moments about the second cross-section axis at the element ends.

Set AXIS2=TYPE3 for members with distributed transverse loading. Then ![](../graphics/key_eqn00146.gif)=min![](../graphics/key_eqn00147.gif), where ![](../graphics/key_eqn00144.gif) is the compressive axial stress and ![](../graphics/key_eqn00148.gif) is the Euler buckling stress corresponding to the second cross-section direction.

### **Data line to define the buckling reduction coefficients: **

**First (and only) data line:**

If a blank is given on the data line, it is interpreted as zero. If a blank or zero value is given on the data line and either the AXIS1 or AXIS2 parameter is included for this reduction factor, the parameter value will override the zero value given on the data line. If a nonzero value is given on the data line and the AXIS1 or AXIS2 parameter is specified for the same reduction coefficient, an error is issued.




