# *FLUID INFLATOR ACTIVATION







### *FLUID INFLATOR ACTIVATIONActivate fluid inflator definitions.

This option is used to activate fluid inflator definitions. 

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Inflator definition," Section 11.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID INFLATOR](ch06abk26.md)

### **Optional parameters: **

INFLATION TIME AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining a mapping between the inflation time and the actual time. If this parameter is omitted, the inflation time will be equal to the actual time elapsed since activation. 

MASS FLOW AMPLITUDE

Set this parameter equal to the name of the amplitude curve by which to modify the mass flow rate. This parameter is valid only if the mass flow rate is prescribed directly in the inflator property definition. It will be ignored if the mass flow rate is calculated by using tank test data or the dual pressure method.

OP

Set OP=MOD (default) for existing [*FLUID INFLATOR ACTIVATION](ch06abk27.md) definitions to remain, with this option defining a fluid inflator activation to be added or modified. 

Set OP=NEW if all fluid inflator activations that are currently in effect should be removed. To remove only selected fluid inflator activations, use OP=NEW and respecify all fluid inflator activations that are to be retained.

### **Data lines to define the fluid inflator activation: **

**First line:**

Repeat this data line as often as necessary. Up to 8 entries are allowed per line.




