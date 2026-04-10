# *CONTACT PROPERTY ASSIGNMENT







### *CONTACT PROPERTY ASSIGNMENTAssign contact properties for the general contact algorithm.

This option is used to modify contact properties for specific contact interactions within the domain considered by general contact. It must be used in conjunction with the [*CONTACT](ch03abk54.md) and [*SURFACE INTERACTION](ch18abk50.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; Model or history data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Model or Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Contact properties for general contact in Abaqus/Standard," Section 36.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpropassignstd)
- ["Assigning contact properties for general contact in Abaqus/Explicit," Section 36.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpropassign)
- [*CONTACT](ch03abk54.md)
- [*SURFACE INTERACTION](ch18abk50.md)

**There are no parameters associated with this option.**

### **Data lines to assign nondefault contact properties: **

**First line:**

Repeat this data line as often as necessary. If the contact property assignments overlap, the last assignment applies in the overlap region.




