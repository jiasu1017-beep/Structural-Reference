# *GAS SPECIFIC HEAT







### *GAS SPECIFIC HEATDefine reacted product's specific heat for an ignition and growth equation of state.

This option is used to specify the specific heat of reacted gas products for an ignition and growth equation of state. It is required when the [*EOS](ch05abk27.md), TYPE=IGNITION AND GROWTH option is used. The [*GAS SPECIFIC HEAT](ch07abk07.md) option should appear immediately after the [*EOS](ch05abk27.md) or the [*REACTION RATE](ch17abk10.md) option.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Equation of state," Section 25.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ceos)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the reacted product's specific heat. If this parameter is omitted, it is assumed that the reacted product's specific heat is constant or depends only on temperature. 

### **Data lines to specify the reacted product's specific heat: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the specific heat as a function of temperature and other predefined field variables.




