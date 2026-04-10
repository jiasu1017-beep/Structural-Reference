# *SURFACE SECTION







### *SURFACE SECTIONSpecify section properties for surface elements.

This option is used to specify a surface element cross-section. It must be used in conjunction with the [*REBAR LAYER](ch17abk12.md) option. In an Abaqus/Aqua analysis the surface section can be used to visualize the behavior of the water surface under gravity waves.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  Abaqus/Aqua  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Surface elements," Section 32.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esurface)
- ["Defining reinforcement," Section 2.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebarlayer)
- [*REBAR LAYER](ch17abk12.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the surface elements for which the section properties are being defined.

### **Optional, mutually exclusive parameters: **

AQUAVISUALIZATION

This parameter applies only to Abaqus/Aqua analyses.

Set AQUAVISUALIZATION=YES to specify that the referenced surface elements will be used to visualize gravity waves.

DENSITY

Set this parameter equal to the mass density per unit area of the surface element section.

**There are no data lines associated with this option.**



