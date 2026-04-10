# *SORPTION







### *SORPTIONDefine absorption and exsorption behavior.

This option is used to define absorption and exsorption behaviors of a partially saturated porous medium in the analysis of coupled wetting liquid flow and porous medium stress.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Sorption," Section 26.6.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-csorption)

### **Optional parameters: **

LAW

Set LAW=LOG to define the absorption or exsorption behavior by the analytical logarithmic form.

 Set LAW=TABULAR (default) to define the absorption or exsorption behavior in tabulated form.

TYPE

Set TYPE=ABSORPTION (default) to define the absorption behavior. 

 Set TYPE=EXSORPTION to define the exsorption behavior (this must be a repeated use of the option for the same material).

 Set TYPE=SCANNING to define the scanning line (this must be a repeated use of the option for the same material).

### **Data lines for TYPE=ABSORPTION or TYPE=EXSORPTION and LAW=TABULAR: **

**First line:**

Repeat this data line as often as necessary to define the relationship between ![](../graphics/key_eqn00847.gif) and *s* from ![](../graphics/key_eqn01079.gif) to ![](../graphics/key_eqn00897.gif) in increasing values of *s*. At least two data lines must be specified.

### **Data line for TYPE=ABSORPTION or TYPE=EXSORPTION and LAW=LOG: **

**First (and only) line:**

### **Data line for TYPE=SCANNING: **

**First (and only) line:**




