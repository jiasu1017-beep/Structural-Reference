# *DENSITY







### *DENSITYSpecify material mass density.

This option is used to define a material's mass density. In an Abaqus/Standard analysis spatially varying mass density can be defined for solid continuum elements using a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Density," Section 21.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdensity)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the density, in addition to temperature. If this parameter is omitted, it is assumed that the density is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

This parameter is not relevant in an Abaqus/Standard analysis if spatially varying density is defined using a distribution. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions). 

 It is assumed that the density is constant in Abaqus/CFD analyses.

PORE FLUID

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the density of the pore fluid in a porous medium is being defined.

### **Data lines to define mass density: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the density as a function of temperature and other predefined field variables.

### **Data line to define spatially varying mass density for solid continuum elements in an Abaqus/Standard analysis using a distribution: **

**First (and only) line:**




