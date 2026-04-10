# *CFLOW







### *CFLOWSpecify concentrated fluid flow.

This option is used to apply concentrated fluid flow to any node  including phantom nodes in enriched elements in consolidation problems.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Coupled pore fluid diffusion and stress analysis," Section 6.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupdiffstress)
- ["Geostatic stress state," Section 6.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ageostatstress)
- ["Pore fluid flow," Section 34.4.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pporousflow)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the flow during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*CFLOW](ch03abk15.md)s to remain, with this option modifying existing concentrated flows or defining additional concentrated flows.

Set OP=NEW if all existing [*CFLOW](ch03abk15.md)s applied to the model should be removed.

PHANTOM

This parameter applies only to enriched elements in Abaqus/Standard.

Set PHANTOM=NODE to apply concentrated flows to a phantom node that is originally located coincident with the specified real node in an enriched element.

Set PHANTOM=EDGE to apply concentrated flows to a phantom node located at an element edge between the two specified real corner nodes in an enriched element.

### **Data lines to define concentrated flow when the PHANTOM parameter is not used: **

**First line:**

Repeat this data line as often as necessary to define concentrated flows.

### **Data lines to define concentrated flow when PHANTOM=NODE: **

**First line:**

Repeat this data line as often as necessary to define concentrated flows.

### **Data lines to define concentrated flow when PHANTOM=EDGE: **

**First line:**

Repeat this data line as often as necessary to define concentrated flows.




