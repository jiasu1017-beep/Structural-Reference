# *CONTACT PERMEABILITY







### *CONTACT PERMEABILITYSpecify fluid permeability contact property.

This option is used to modify pore fluid permeability in a surface interaction model. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option. If this option is omitted, the surface interaction model will have no resistance to fluid flow across a contact interface (corresponding to infinite permeability) while contact is active and for clearances up to a default tolerance distance.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Pore fluid contact properties," Section 37.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aporefluidinteraction)
- ["Coupled pore fluid diffusion and stress analysis," Section 6.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupdiffstress)
- [*SURFACE INTERACTION](ch18abk50.md)
- [*SOILS](ch18abk21.md)

### **Optional parameters: **

CUTOFF FLOW ACROSS

Set this parameter equal to a cutoff clearance distance above which no fluid flow occurs across a contact interface.

CUTOFF GAP FILL

Set this parameter equal to a cutoff clearance distance above which no fluid flow occurs into or out of a contact interface due to changes in clearance distance.

DEPENDENCIES

Set this parameter equal to the number of field variables on which the contact permeability, ![](../graphics/key_eqn00372.gif), depends.

### **Data lines to define the contact permeability, ![](../graphics/key_eqn00372.gif), directly: **

**First line:**

Repeat this data line as often as necessary to define the dependence of contact permeability on the contact pressure, average surface pore pressure, average surface temperature, and the average of any predefined field variables on the surfaces.




