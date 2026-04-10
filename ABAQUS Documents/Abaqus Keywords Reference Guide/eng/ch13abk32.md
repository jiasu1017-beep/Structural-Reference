# *M1







### *M1Define the first bending moment behavior of beams.

This option is used to define the first bending moment behavior of beams. It can be used only in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md), SECTION=NONLINEAR GENERAL option.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Using a general beam section to define the section behavior," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- [*BEAM GENERAL SECTION](ch02abk05.md)

### **Optional parameters (if neither ELASTIC nor LINEAR is included, elastic-plastic response is assumed): **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the moment-curvature relationship, in addition to temperature. If this parameter is omitted, it is assumed that the moment–curvature relationship is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

ELASTIC

Include this parameter if the bending moment–curvature relationship is nonlinear but elastic.

LINEAR

Include this parameter if the bending moment varies linearly with curvature.

### **Data lines if the LINEAR parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the bending stiffness as a function of temperature and other predefined field variables.

### **Data lines if the LINEAR parameter is omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the bending moment–curvature relationship as a function of temperature and other predefined field variables.




