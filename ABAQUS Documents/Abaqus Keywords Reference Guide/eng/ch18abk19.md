# *SLIDE LINE







### *SLIDE LINESpecify slide line surfaces on which deformable structures may interact.

This option is relevant only for slide line and tube-to-tube contact elements. It is used to define the slide line and to specify which set of contact elements interacts with it.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Assembly  

**Abaqus/CAE: **Unsupported; the Interaction module uses surface-based contact. 

##### **References:**

- ["Tube-to-tube contact elements," Section 40.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eitt)
- ["Slide line contact elements," Section 40.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eslidelineelem)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the slide line or tube-to-tube contact elements that interact with the slide line being defined.

TYPE

Set TYPE=LINEAR to define a slide line made up of linear segments. This parameter should be used when first-order elements make up the model.

Set TYPE=PARABOLIC to define a slide line made up of parabolic segments. This parameter should be used when second-order elements make up the model. In this case the slide line should consist of an odd number of nodes, where the odd nodes on the slide line are associated with the ends of parabolic segments.

### **Optional parameters: **

EXTENSION ZONE

Set this parameter equal to a fraction of the end segment length by which either end of an open slide line is to be extended to avoid numerical round off errors associated with contact modeling. The value given must lie between 0.0 and 0.2. The default value is 0.1.

GENERATE

Include this parameter to allow incremental generation of node numbers along a slide line.

SMOOTH

Set this parameter equal to the smoothing fraction, *f*, to round discontinuities between line segments of a slide line. The default is 0. The limit is ![](../graphics/key_eqn01076.gif).

### **Data lines if the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary to specify the nodes forming the slide line. Enter up to 16 integer values per line.

### **Data lines if the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary to specify the nodes forming the slide line.




