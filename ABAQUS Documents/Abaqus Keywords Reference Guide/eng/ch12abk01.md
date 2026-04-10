# *LATENT HEAT







### *LATENT HEATSpecify latent heats.

This option is used to specify a material's latent heat.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Latent heat," Section 26.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-clatentheat)

### **Optional parameter: **

PORE FLUID

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the latent heat of the pore fluid in a porous medium is being defined.

### **Data lines to define a material's latent heat: **

**First line:**

Repeat this data line as often as necessary to define phase changes in the material; one line per phase change. Latent heat values must be given in ascending order of temperature.




