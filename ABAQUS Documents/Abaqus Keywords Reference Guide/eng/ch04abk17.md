# *DESIGN RESPONSE







### *DESIGN RESPONSESpecify responses for design sensitivity analysis.

This option is used to write the sensitivities of contact, element, nodal, and/or eigenmode responses to the output database. The [*CONTACT RESPONSE](ch03abk72.md), [*ELEMENT RESPONSE](ch05abk11.md), and/or [*NODE RESPONSE](ch14abk13.md) options can be used in conjunction with this option.

**Product: **Abaqus/Design  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*CONTACT RESPONSE](ch03abk72.md)
- [*ELEMENT RESPONSE](ch05abk11.md)
- [*NODE RESPONSE](ch14abk13.md)

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency of the response sensitivities. The output will always be written to the output database at the last increment. If this parameter is omitted, output will be written at every increment of the analysis. Set FREQUENCY=0 to suppress output of the response sensitivities. This parameter also controls the frequency of the sensitivity calculations for the total DSA formulation.

MODE LIST

Include this parameter to indicate that a list of eigenmodes for which sensitivities are desired will be listed on the data lines. This parameter is valid only in a [*FREQUENCY](ch06abk35.md) procedure.

### **Data lines to list desired eigenmodes if the MODE LIST parameter is included: **

**First line:**

Repeat this data line as often as necessary to list all desired eigenmodes.




