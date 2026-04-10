# *GAP RADIATION







### *GAP RADIATIONIntroduce heat radiation between surfaces.

This option is used to provide radiative heat transfer between closely adjacent surfaces. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option or in an Abaqus/Standard analysis with the [*GAP](ch07abk01.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Part,  Part instance,  Assembly,  Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)

**There are no parameters associated with this option.**

### **Data lines to define surface constants for radiative heat transfer: **

**First line:**

**Second line:**

Repeat this data line as often as necessary to define the dependence of the view factor on gap clearance.




