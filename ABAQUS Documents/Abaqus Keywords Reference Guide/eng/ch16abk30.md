# *PRE-TENSION SECTION







### *PRE-TENSION SECTIONAssociate a pre-tension node with a pre-tension section.

This option is used to associate a pre-tension node with a pre-tension section.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Prescribed assembly loads," Section 34.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ppretension)

### **Required parameter: **

NODE

Set this parameter equal to either the pre-tension node number or the name of a node set containing the pre-tension node. If the name of a node set is chosen, the node set must contain exactly one node.

### **Required, mutually exclusive parameters: **

ELEMENT

Set this parameter equal to either the element number of the truss or beam element used to define the pre-tension section or the name of an element set containing the truss or beam element used to define the pre-tension section. If the name of an element set is chosen, the element set must contain exactly one element.

SURFACE

Set this parameter equal to the name of the surface definition ([*SURFACE](ch18abk47.md)) that defines the pre-tension section (when continuum elements are used).

### **Data line to define the normal to the section (optional): **

**First (and only) data line:**

If the data line is omitted, Abaqus/Standard will compute an average normal to the pre-tension section for continuum elements. For truss or beam elements the default normal points from the first to the last node in the element connectivity.




