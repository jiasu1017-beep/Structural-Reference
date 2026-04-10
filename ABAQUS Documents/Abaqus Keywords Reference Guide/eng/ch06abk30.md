# *FLUID LEAKOFF







### *FLUID LEAKOFFDefine fluid leak-off coefficients for pore pressure cohesive elements.

This option is used to define leak-off coefficients for pore pressure cohesive elements. 

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Defining the constitutive response of fluid within the cohesive element gap," Section 32.5.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivefluidbehavior)
- ["UFLUIDLEAKOFF," Section 1.1.34 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uufluidleakoff)

### **Optional, mutually exclusive parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the fluid leak-off coefficients, in addition to temperature. If this parameter is omitted, it is assumed that the leak-off coefficients are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

USER

Include this parameter to indicate that user subroutine [`UFLUIDLEAKOFF`](../sub/sub-link.md#sub-xsl-ufluidleakoff) will be used to define the fluid leak-off coefficients.

### **Data lines to define fluid leak-off coefficients if the USER parameter is omitted: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to specify *K* as a function of temperature and field variables.

### **There are no data lines when the USER parameter is included. **




