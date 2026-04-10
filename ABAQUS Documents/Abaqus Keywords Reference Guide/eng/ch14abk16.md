# *NORMAL







### *NORMALSpecify a particular normal direction.

This option is used to define alternative nodal normals for elements. In an Abaqus/Standard analysis it can also be used to define alternative normals for contact surfaces.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

##### **Reference:**

- ["Normal definitions at nodes," Section 2.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inodalnormals)

### **Optional parameter: **

TYPE

Set TYPE=ELEMENT (default) to allow the alternative normal definition of elements.

Set TYPE=CONTACT SURFACE to allow the alternative normal definition of contact surfaces in an Abaqus/Standard analysis.

### **Data lines to define normals for elements (TYPE=ELEMENT): **

**First line:**

Repeat this data line as often as necessary to define the normals.

### **Data lines to define normals for contact surfaces (TYPE=CONTACT SURFACE): **

**First line:**

Repeat this data line as often as necessary to define the normals.




