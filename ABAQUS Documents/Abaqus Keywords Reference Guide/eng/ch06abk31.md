# *FLUID SECTION







### *FLUID SECTIONSpecify element properties for fluid and porous media elements.

This option is used to define the properties of fluid elements and porous media elements.

**Products: **Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Fluid (continuum) elements," Section 28.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecfdelem)
- ["Fluid element library," Section 28.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecfdelemlibrary)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the elements for which the material behavior is being defined.

### **Optional parameter: **

TYPE

Set TYPE=SINGLE FLUID (default) for single-phase fluid flow.

Set TYPE=POROUS MEDIA for heat transfer analysis involving porous media.

### **Data line to define fluid elements for single-phase fluid flow: **

**First (and only) line:**

### **Data lines to define porous media elements for heat transfer analysis: **

**First line:**

**Second line:**




