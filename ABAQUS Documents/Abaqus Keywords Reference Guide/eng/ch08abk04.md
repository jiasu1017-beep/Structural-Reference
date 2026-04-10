# *HEATCAP







### *HEATCAPSpecify a point capacitance.

This option is used to define lumped heat capacitance values associated with HEATCAP elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module.

##### **Reference:**

- ["Point capacitance," Section 30.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecapacitance)

### **Required parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the point capacitance. If this parameter is omitted, it is assumed that the point capacitance is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

ELSET

Set this parameter equal to the name of the element set containing the HEATCAP elements for which the value is being given.

### **Data lines to define the capacitance magnitude: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the point capacitance as a function of temperature and other predefined field variables. Abaqus does not use any specific physical units, so the user's choice must be consistent.




