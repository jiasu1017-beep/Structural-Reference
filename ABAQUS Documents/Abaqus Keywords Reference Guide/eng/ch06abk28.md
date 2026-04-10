# *FLUID INFLATOR MIXTURE







### *FLUID INFLATOR MIXTUREDefine gas species used for a fluid inflator.

This option is used to define the gas species used for a fluid inflator. The [*FLUID INFLATOR MIXTURE](ch06abk28.md) option can be used only in conjunction with the [*FLUID INFLATOR PROPERTY](ch06abk29.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)
- ["Inflator definition," Section 11.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID BEHAVIOR](ch06abk16.md)
- [*FLUID INFLATOR PROPERTY](ch06abk29.md)

### **Required parameter: **

NUMBER SPECIES

Set this parameter equal to the number of gas species used for this inflator.

### **Optional parameter: **

TYPE

Set TYPE=MASS FRACTION (default) to use the mass fraction for a mixture of ideal gases.

Set TYPE=MOLAR FRACTION to use the molar fraction for a mixture of ideal gases.

### **Data lines to define gas species for a fluid inflator: **

**First line:**

Repeat this data line as often as necessary to define all gas species for this inflator.

**Next line:**

**Subsequent lines (only needed if the NUMBER SPECIES parameter has a value greater than seven):**

Repeat this set of data lines as often as necessary to define the mass fraction or molar fraction as a function of inflation time.




