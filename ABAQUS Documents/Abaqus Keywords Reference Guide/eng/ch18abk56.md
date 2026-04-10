# *SWELLING







### *SWELLINGSpecify time-dependent volumetric swelling.

This option is used to specify time-dependent metal swelling for a material. Swelling behavior defined by this option is active only during [*SOILS](ch18abk21.md), CONSOLIDATION; [*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md); and [*VISCO](ch21abk03.md) procedures.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["CREEP," Section 1.1.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ucreep)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the volumetric swelling strain rate in addition to temperature. If this parameter is omitted, it is assumed that the volumetric swelling strain rate is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=INPUT (default) to define the swelling behavior on the data lines. 

Set LAW=USER to define the swelling behavior in user subroutine [`CREEP`](../sub/sub-link.md#sub-xsl-creep).

### **Data lines for LAW=INPUT: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of volumetric swelling strain rate on temperature and other predefined field variables.




