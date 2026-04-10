# *FLUID EXCHANGE ACTIVATION







### *FLUID EXCHANGE ACTIVATIONActivate fluid exchange definitions.

This option is used to activate fluid exchange definitions between two fluid cavities or between a fluid cavity and its environment.

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)
- ["Fluid exchange definition," Section 11.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE](ch06abk21.md)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining a multiplier for the fluid exchange magnitude. See ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude).

BLOCKAGE

Set BLOCKAGE=YES to consider vent and leakage area obstruction by contacted surfaces. The default value is BLOCKAGE=NO.

DELTA LEAKAGE AREA

Set this parameter equal to the ratio of the actual surface area over the initial surface area at which you want the fluid to leak. This real value should be positive and greater than or equal to one. The effective surface area used for the fluid exchange is the difference between the actual area of the surface and the area of the surface at the beginning of step.

OP

Set OP=MOD (default) for existing [*FLUID EXCHANGE ACTIVATION](ch06abk22.md) definitions to remain, with this option defining a fluid exchange activation to be added or modified. 

Set OP=NEW if all fluid exchange activations that are currently in effect should be removed. To remove only selected fluid exchange activations, use OP=NEW and respecify all fluid exchange activations that are to be retained.

OUTFLOW ONLY

Include this parameter if the flow is allowed only from the first fluid cavity to the second fluid cavity defined in the [*FLUID EXCHANGE](ch06abk21.md) option.

If this parameter is omitted, the flow is allowed from both directions. The reference nodes defined on the data line on the [*FLUID EXCHANGE](ch06abk21.md) option should be in the appropriate order to obtain the desired flow direction.

### **Data lines to define the fluid exchange activation: **

**First line:**

Repeat this data line as often as necessary. Up to 8 entries are allowed per line.




