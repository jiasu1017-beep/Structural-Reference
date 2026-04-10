# *CONWEP CHARGE PROPERTY







### *CONWEP CHARGE PROPERTYDefine a CONWEP charge for incident waves.

This option defines parameters that create the time history of pressure loading used to simulate an explosion in air. This option must be used in conjunction with the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) option. The pressure loading is calculated using the CONWEP model empirical data in which mass, length, time, and pressure are given in specific units. Multiplication factors are defined for conversion between the CONWEP data units and the analysis units.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md)

**There are no parameters associated with this option.**

### **Data lines to define the CONWEP charge properties: **

**First line:**

**Second line (enter a blank line if the analysis uses SI units):**




