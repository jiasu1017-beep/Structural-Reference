# *NODAL THICKNESS







### *NODAL THICKNESSDefine shell or membrane thickness at nodes.

This option is used to define variable shell or membrane thicknesses on a nodal basis. The thickness data defined with this option will be ignored unless the NODAL THICKNESS parameter is included on either the [*SHELL GENERAL SECTION](ch18abk14.md) or the [*SHELL SECTION](ch18abk15.md) options for shell elements or on the [*MEMBRANE SECTION](ch13abk16.md) option for membrane elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Nodal thicknesses," Section 2.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inodalthickness)
- ["Membrane elements," Section 29.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-emembrane)
- ["Using a shell section integrated during the analysis to define the section behavior," Section 29.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellsection)
- ["Using a general shell section to define the section behavior," Section 29.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellgensect)
- ["Line spring elements for modeling part-through cracks in shells," Section 32.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-elinespring)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)

### **Optional parameters: **

GENERATE

Include this parameter to interpolate the thickness between two bounding nodes or node sets. The thickness for the bounding nodes or node sets must have been defined earlier. If the node sets do not have the same number of nodes, the extra nodes in the longer set are ignored.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines when the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary to define the variation in shell or membrane thickness.

### **Data lines when the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary to define the variation in thickness.




