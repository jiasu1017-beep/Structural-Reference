# *CREEP STRAIN RATE CONTROL







### *CREEP STRAIN RATE CONTROLControl loadings based on the maximum equivalent creep strain rate.

This option is used to control loading based on a maximum equivalent creep strain rate calculated in a specified element set.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)

### **Required parameters: **

AMPLITUDE

Set this parameter equal to the [*AMPLITUDE](ch01abk09.md) name (of type DEFINITION=SOLUTION DEPENDENT) that is referenced by the loads being controlled (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

ELSET

Set this parameter equal to the name of the element set in which the search for the maximum equivalent creep strain rate is made. The [*CREEP](ch03abk85.md) option must be part of the [*MATERIAL](ch13abk08.md) definition (["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)) for some elements in the set.

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the target creep strain rate, in addition to temperature and creep strain. If this parameter is omitted, it is assumed that the target creep strain rate depends only on the equivalent creep strain and, possibly, on temperature. The creep strain dependency curve at each temperature must always start at zero equivalent creep strain. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

OP

Set OP=MOD (default) for existing target [*CREEP STRAIN RATE CONTROL](ch03abk86.md) definitions to remain, with this option defining target creep strain rates to be added or modified.

 Set OP=NEW if all target creep strain rates defined in the previous step should be removed.

### **Data lines to define load control parameters: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of target strain rate on creep strain, temperature, and other predefined field variables.




