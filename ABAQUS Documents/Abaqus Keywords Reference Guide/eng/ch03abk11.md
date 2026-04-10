# *CECURRENT







### *CECURRENTSpecify concentrated current in an electric conduction analysis.

This option is used to apply concentrated current to any node of a model in coupled thermal-electrical and coupled thermal-electrical-structural analyses.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)
- ["Fully coupled thermal-electrical-structural analysis," Section 6.7.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the current during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*CECURRENT](ch03abk11.md)s to remain, with this option modifying existing concentrated currents or defining additional concentrated currents. 

Set OP=NEW if all existing [*CECURRENT](ch03abk11.md)s applied to the model should be removed.

### **Data lines to define concentrated current at nodes: **

**First line:**

Repeat this data line as often as necessary to define current at various nodes or node sets.




