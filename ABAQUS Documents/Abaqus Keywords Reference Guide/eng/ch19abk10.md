# *TRACER PARTICLE







### *TRACER PARTICLEDefine tracer particles for tracking the location of and results at material points during a step.

This option is used to define tracer particles and assign them to tracer sets for tracking the location of and results at material points during a step. The tracer set name is used in conjunction with the [*ELEMENT OUTPUT](ch05abk10.md) and/or the [*NODE OUTPUT](ch14abk11.md) options to request output for the tracer particles associated with the tracer set name. 

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*ELEMENT OUTPUT](ch05abk10.md)
- [*NODE OUTPUT](ch14abk11.md)

### **Required parameter: **

TRACER SET

Set this parameter equal to the name of the tracer set to which these tracer particles will be assigned.

### **Optional parameter: **

PARTICLE BIRTH STAGES

Set this parameter equal to the number of tracer particle births within the step. If this parameter is omitted, a single particle birth will occur at the beginning of the step. If this parameter has a value *n* greater than one, tracer particles will leave their parent nodes *n* times during the step at equally spaced intervals in time.

### **Data lines to define the tracer particles associated with the tracer set: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.




