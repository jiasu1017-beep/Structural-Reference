# *CONNECTOR SECTION







### *CONNECTOR SECTIONSpecify connector attributes for connector elements.

This option is used to define the attributes of connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector elements," Section 31.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorelem)
- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the connector elements for which the connection attributes are being defined.

### **Optional parameters: **

BEHAVIOR

Set this parameter equal to the name of the connector behavior that defines these connector elements. If this parameter is omitted, the connector element's behavior is determined by kinematic constraints only.

CONTROLS

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used for the connector elements.

Section controls can be used to specify whether the connector elements should be deleted once they fail completely. If this parameter is omitted, the failed elements will not be deleted. Section controls can also be used to specify a maximum value of the scalar degradation (damage) parameter, ![](../graphics/key_eqn00358.gif), and to specify the viscosity coefficient, ![](../graphics/key_eqn00195.gif), for viscous damping or regularization.

ELIMINATION

This parameter applies only to Abaqus/Explicit analyses.

Set ELIMINATION=NO (default) if the constraint or kinetic forces/moments of the associated connector elements are to be solved for directly in the implicit constraint solver in Abaqus/Explicit.

Set ELIMINATION=YES if the constraint or kinetic forces/moments of the associated connector elements are to be solved for using a condensation technique.

### **Data lines to define the connection attributes: **

**First line:**

**Second line (optional):**

Omit the second line if neither of the two orientations is specified and the third line is omitted. Leave blank if neither of the two orientations is specified and the third line is included.

**Third line (optional) for SLIPRING connection type:**

Omit the third line if no data are specified.

**Third line (optional) for RETRACTOR or FLOW-CONVERTER connection types:**

Omit the third line if no data are specified.




