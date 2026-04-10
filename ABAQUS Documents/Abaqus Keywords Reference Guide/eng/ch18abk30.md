# *SRADIATE







### *SRADIATESpecify surface radiation conditions in heat transfer analysis.

This option is used to apply surface radiation boundary conditions between a nonconcave surface and a nonreflecting environment in fully coupled thermal-stress analysis or to define an approximate cavity radiation interaction. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

It must be used in conjunction with the [*PHYSICAL CONSTANTS](ch16abk09.md) option, which is used to define the Stefan-Boltzmann constant.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the ambient temperature with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step.

OP

Set OP=MOD (default) for existing [*SRADIATE](ch18abk30.md) definitions to remain, with this option modifying existing radiation conditions or defining additional radiation conditions. 

Set OP=NEW if all existing [*SRADIATE](ch18abk30.md) definitions applied to the model should be removed.

### **Data lines to define surface radiation conditions: **

**First line:**

Repeat this data line as often as necessary to define radiation conditions for different surfaces.

### **Data lines to define approximate cavity radiation (available only in Abaqus/Standard): **

**First line:**

Repeat this data line as often as necessary to define radiation conditions for different surfaces.




