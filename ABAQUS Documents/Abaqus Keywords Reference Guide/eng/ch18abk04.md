# *SECTION POINTS







### *SECTION POINTSLocate points in the beam section for which stress and strain output are required.

This option is used as model data in Abaqus/Standard and Abaqus/Explicit in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md) option and as history data in Abaqus/Standard in conjunction with the [*BEAM SECTION GENERATE](ch02abk07.md) option.

When used in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md) option and a predefined library section, it locates section points in the beam section for which axial stress and axial strain output are required.

When used in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md), SECTION=MESHED option, it locates elements and integration points in the beam cross-section model for which stress and strain output are required and provides material data and derivatives of the warping function required for determining stress and strain output.

When used in conjunction with the [*BEAM SECTION GENERATE](ch02abk07.md) option, it associates a user-defined section point label with elements and integration points in the beam cross-section model for which stress and strain output are required during the subsequent beam analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Part,  Part instance,  Step

**Abaqus/CAE: **Property module

##### **References:**

- ["Using a general beam section to define the section behavior," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- ["Meshed beam cross-sections," Section 10.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ameshedsection)
- [*BEAM GENERAL SECTION](ch02abk05.md)

**There are no parameters associated with this option.**

### **Data lines to locate section points for output when used in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md) option and a predefined library section: **

**First line:**

Continue giving ![](../graphics/key_eqn01050.gif) coordinate pairs for as many points as needed. At most four pairs of points can be specified on any data line. If the point (0,0) is specified as the last entry on a line, it will be ignored unless it is the only point requested.

### **Data lines to locate elements and integration point numbers for meshed sections when used in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md), SECTION=MESHED option: **

**First line:**

**Second line:**

 Repeat this set of data lines for as many integration points as needed.

### **Data lines to locate elements and integration point numbers in the cross-section model when used in conjunction with the [*BEAM SECTION GENERATE](ch02abk07.md) option: **

**First line:**

Repeat this data line as often as necessary to specify the elements and integration points.




