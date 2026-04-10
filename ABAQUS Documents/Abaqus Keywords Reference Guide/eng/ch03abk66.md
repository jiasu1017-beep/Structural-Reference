# *CONTACT INTERFERENCE







### *CONTACT INTERFERENCEPrescribe time-dependent allowable interferences of contact pairs and contact elements.

This option is used to prescribe time-dependent allowable interferences for contact pairs and contact elements. It is useful for solving problems where there are large initial overclosures of the contacting bodies.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Modeling contact interference fits in Abaqus/Standard," Section 36.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactinterference)
- ["Adjusting initial surface positions and specifying initial clearances in Abaqus/Standard contact pairs," Section 36.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aadjustsurfaces)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the prescribed interference during the step. If this parameter is omitted, the prescribed interference is applied immediately at the beginning of the step and ramped down to zero linearly over the step.

OP

Set OP=MOD (default) for existing [*CONTACT INTERFERENCE](ch03abk66.md) definitions to remain, with this option defining a contact interference to be added or modified. Set OP=NEW if all [*CONTACT INTERFERENCE](ch03abk66.md) definitions defined in previous steps should be removed.

SHRINK

Include this parameter to invoke the automatic shrink fit capability. This capability can be used only in the first step of an analysis. When this parameter is included, no data are required other than the contact pairs or elements to which the option is applied. In addition, any AMPLITUDE reference specified will be ignored.

TYPE

Use this parameter to specify whether the prescribed interference will be applied to contact pairs or contact elements. Set TYPE=CONTACT PAIR (default) to specify a contact interference for contact pairs. Set TYPE=ELEMENT to specify a contact interference for contact elements.

### **Data lines to define an allowable contact interference for a contact pair (TYPE=CONTACT PAIR): **

**First line:**

Repeat this data line as often as necessary to specify additional contact pairs. Each line defines a distinct contact interference between one contact pair.

### **Data lines to define an allowable contact interference for contact elements (TYPE=ELEMENT): **

**First line:**

Repeat this data line as often as necessary to specify additional element sets containing contact elements.




