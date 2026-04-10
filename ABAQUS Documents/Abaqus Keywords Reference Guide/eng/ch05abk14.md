# *EMBEDDED ELEMENT







### *EMBEDDED ELEMENTSpecify an element or a group of elements that lie embedded in a group of "host" elements in a model.

This option is used to specify an element or a group of elements that lie embedded in a group of “host” elements in a model.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Embedded elements," Section 35.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pembeddedelement)

### **Optional parameters: **

ABSOLUTE EXTERIOR TOLERANCE

Set this parameter equal to the absolute value (given in the units used in the model) by which a node on the embedded element may lie outside the region of the host elements in the model. If this parameter is omitted or has a value of 0.0, the EXTERIOR TOLERANCE will apply.

EXTERIOR TOLERANCE

Set this parameter equal to the fraction of the average size of all the non-embedded elements in the model by which a node of the embedded element may lie outside the region of the host elements. The default is 0.05.

If both exterior tolerance parameters are specified by the user, Abaqus will use the smaller of the two tolerances.

HOST ELSET

Set this parameter equal to the name of the host element set in which the specified elements on the data lines are to be embedded. If this parameter is omitted, Abaqus will search all non-embedded elements in the model that lie in the vicinity of specified embedded elements.

PARTIAL EMBED

Set this parameter equal to YES if the host elements are expected to only partially embed the embedded elements. The default is NO.

ROUNDOFF TOLERANCE

Set this parameter equal to a small value below which the weight factors of the nodes on a host element associated with an embedded node will be zeroed out. The small weight factors will be distributed to the other nodes on the host element in proportion to their initial weights. The position of the embedded node will also be adjusted accordingly. The default value is 106.

### **Data lines to define the elements embedded in the host elements: **

**First line:**

Repeat this data line as often as necessary.




