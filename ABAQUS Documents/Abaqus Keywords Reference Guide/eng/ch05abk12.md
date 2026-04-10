# *ELGEN







### *ELGENIncremental element generation.

This option is used to generate elements incrementally.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Not applicable; elements are generated when you mesh the model.

##### **Reference:**

- ["Element definition," Section 2.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ielement)

### **Optional parameters: **

ALL NODES

Include this parameter to increment the node numbers of rigid body reference nodes for IRS-type and drag chain elements and nodes used to define the direction of the first cross-section axis for beams in space. By default, these node numbers will not be incremented.

ELSET

Set this parameter equal to the name of the element set to which the elements, including the master element, will be assigned.

### **Data lines to generate elements incrementally: **

**First line:**

Repeat this data line as often as necessary. Each line will generate *N1* *N2* *N3* elements, where *N1* is the number of elements in a row, *N2* is the number of rows in a layer, and *N3* is the number of layers.




