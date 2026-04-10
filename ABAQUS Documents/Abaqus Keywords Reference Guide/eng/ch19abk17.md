# *TURBULENCE MODEL







### *TURBULENCE MODELSpecify turbulence models for fluid analyses.

This option can be used only as a suboption of the [*CFD](ch03abk13.md) option to enable turbulence modeling for fluid flow simulations.

**Products: **Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **Required parameter: **

TYPE

Set TYPE=SPALART ALLMARAS to specify the Spalart-Allmaras turbulence model.

Set TYPE=RNG KEPSILON  to specify the ![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00849.gif) renormalization group turbulence model.

Set TYPE=KEPSILON REALIZABLE to specify the ![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00849.gif) realizable turbulence model.

Set TYPE=KOMEGA SST to specify the ![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00018.gif)  shear-stress transport turbulence model.

### **Data lines for TYPE=SPALART ALLMARAS: **

**First line:**

**Second line:**

**Third line (enter a blank line unless ENERGY EQUATION=TEMPERATURE is used in the associated [*CFD](ch03abk13.md) option):**

### **Data lines for TYPE=RNG KEPSILON: **

**First line:**

**Second line (enter a blank line unless ENERGY EQUATION=TEMPERATURE is used in the associated [*CFD](ch03abk13.md) option):**

### **Data lines for TYPE=KEPSILON REALIZABLE: **

**First line:**

**Second line:**

**Third line (enter a blank line unless ENERGY EQUATION=TEMPERATURE is used in the associated [*CFD](ch03abk13.md) option):**

### **Data lines for TYPE=KOMEGA SST: **

**First line:**

**Second line (enter a blank line unless ENERGY EQUATION=TEMPERATURE is used on the associated [*CFD](ch03abk13.md) option):**




