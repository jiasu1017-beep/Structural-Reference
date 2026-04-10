# *SPECIFIC HEAT







### *SPECIFIC HEATDefine specific heat.

This option is used to specify a material's specific heat.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Specific heat," Section 26.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cspecificheat)

### **Optional parameters: **

DEPENDENCIES

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses.

Set this parameter equal to the number of field variables included in the definition of specific heat. If this parameter is omitted, it is assumed that the specific heat is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information. 

PORE FLUID

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the specific heat of the pore fluid in a porous medium is being defined.

TYPE

This parameter applies only to Abaqus/CFD analyses.

Set TYPE=CONSTANT VOLUME (default) to define the specific heat at constant volume.

Set TYPE=CONSTANT PRESSURE to define the specific heat at constant pressure when the energy equation is used for thermal-flow problems.

### **Data lines to specify a material's specific heat: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the specific heat as a function of temperature and other predefined field variables.




