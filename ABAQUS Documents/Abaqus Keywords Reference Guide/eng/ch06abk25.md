# *FLUID FLUX







### *FLUID FLUXChange the amount of fluid in a fluid-filled cavity.

This option is used to specify a change in the amount of fluid in a fluid-filled cavity modeled with hydrostatic fluid elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Fluid exchange definition," Section 11.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavityexchange)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude versus time curve that defines the magnitude of the mass flow rate during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step, regardless of the procedure being used in the step.

OP

Set OP=MOD (default) for existing fluid fluxes to remain, with this option defining fluid fluxes to be added (to cavities with no fluid flux loading) or modified (to cavities with fluid flux loading).

Set OP=NEW if all existing fluid fluxes applied to the model should be removed.

### **Data line to define the fluid mass flow rate: **

**First (and only) line:**




