# *IMPORT ELSET







### *IMPORT ELSETImport element set definitions from a previous Abaqus/Explicit or Abaqus/Standard analysis.

This option is used to import element set definitions that were defined in a previous Abaqus/Explicit or Abaqus/Standard analysis. If the [*IMPORT ELSET](ch09abk06.md) option is used, it must appear after the [*IMPORT](ch09abk04.md) option. If this option is omitted or is specified without any data lines, all the element sets relevant to the analysis will be imported.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Transferring results between Abaqus/Explicit and Abaqus/Standard," Section 9.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexptostd)
- [*IMPORT](ch09abk04.md)

**There are no parameters associated with this option.**

### **Data lines to specify element set definitions to be imported: **

**First line:**

Repeat this data line as often as necessary to specify the element set definitions to be imported. Up to 16 element sets can be listed per line.




