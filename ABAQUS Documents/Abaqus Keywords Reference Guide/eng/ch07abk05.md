# *GAP HEAT GENERATION







### *GAP HEAT GENERATIONIntroduce heat generation due to energy dissipation at the interface.

This option is used to modify the default gap heat generation model used to dissipate energy created by nonthermal surface interactions, such as frictional sliding or electric currents. The default is to convert all of the dissipated energy to heat and to distribute it evenly between the two interacting surfaces.

The [*GAP HEAT GENERATION](ch07abk05.md) option must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option or in an Abaqus/Standard analysis with the [*GAP](ch07abk01.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Part,  Part instance,  Assembly,  Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Frictional behavior," Section 37.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afriction)
- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["Electrical contact properties," Section 37.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)

**There are no parameters associated with this option.**

### **Data line to define the gap heat generation: **

**First (and only) line:**




