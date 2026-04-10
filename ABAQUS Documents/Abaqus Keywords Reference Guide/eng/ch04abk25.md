# *DISCRETE SECTION







### *DISCRETE SECTIONSpecify element properties for discrete elements.

This option is used to define properties of discrete elements.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **Reference:**

- ["Discrete element method," Section 15.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ademanalysis)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the elements for which the section is being defined.

DENSITY

Set this parameter equal to a numerical value or to the name of a distribution  (see ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)) to be used with these elements.

SHAPE

This parameter is used to specify the shape of the discrete element.

Set this parameter equal to SPHERE (default).

### **Optional parameter: **

ALPHA

Set this parameter equal to the value of the mass proportional damping factor for discrete elements. The default value is 0.0.

### **Data line for discrete elements: **

**First (and only) line:**




