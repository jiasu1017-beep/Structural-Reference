# *FASTENER PROPERTY







### *FASTENER PROPERTYPrescribe mesh-independent fastener properties.

This option is used to prescribe the properties of a fastener interaction. This option must be used in conjunction with the [*FASTENER](ch06abk05.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Mesh-independent fasteners," Section 35.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afastener)
- [*FASTENER](ch06abk05.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the fastener property.

### **Optional parameter: **

MASS

Set this parameter equal to the additional mass that will be distributed to the fastener nodes.

### **Data lines to specify the fastener properties: **

**First line:**

**Second line:**

Repeat this data line as often as necessary to specify constraints for different degrees of freedom. When the ORIENTATION parameter is specified on the associated [*FASTENER](ch06abk05.md) option, the degrees of freedom are in the specified local system in the initial configuration; otherwise, they are in the default local system. In either case these directions will rotate with the reference node in large-displacement analyses (when the NLGEOM parameter on the [*STEP](ch18abk36.md) option is set equal to YES).




