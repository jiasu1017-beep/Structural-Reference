# *DISTRIBUTING COUPLING







### *DISTRIBUTING COUPLINGSpecify nodes and weighting for distributing coupling elements.

This option is used to define the set of nodes to which forces and mass are distributed according to a specified weighting and to specify the mass of the associated distributing coupling element. The preferred method for defining a distributing constraint is the [*COUPLING](ch03abk83.md) option used in conjunction with the [*DISTRIBUTING](ch04abk27.md) option. A DCOUP* element, together with the [*DISTRIBUTING COUPLING](ch04abk28.md) option, must be used if a point mass at the reference node needs to be distributed as well.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Unsupported; this option has been superseded by coupling constraints used in conjunction with the distributing option.

##### **Reference:**

- ["Distributing coupling elements," Section 32.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-edistcoupling)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the distributing coupling elements that interact with the coupling nodes. This element set can contain more than one element, although this would not be a typical case.

### **Optional parameter: **

MASS

Set this parameter equal to the mass to be distributed to the coupling nodes.

### **Data lines to specify coupling nodes and assign weight factors: **

**First line:**

Repeat this data line as often as necessary. A minimum of two coupling nodes must be specified for each distributing coupling definition.




