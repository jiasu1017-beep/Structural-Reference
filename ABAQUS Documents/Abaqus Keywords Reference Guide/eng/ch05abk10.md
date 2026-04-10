# *ELEMENT OUTPUT







### *ELEMENT OUTPUTDefine output database requests for element variables.

This option is used to write element variables to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **One of the following mutually exclusive parameters is required when the [*ELEMENT OUTPUT](ch05abk10.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option, unless the request is only for whole model output variables: **

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

TRACER SET

This parameter applies only to Abaqus/Explicit analyses using adaptivity.

Set this parameter equal to the name of the tracer set for which this output request is being made.

### **Optional parameters when the [*ELEMENT OUTPUT](ch05abk10.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), FIELD option: **

DIRECTIONS

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses.

Set DIRECTIONS=YES (default) to write the element material directions to the output database. Set DIRECTIONS=NO to indicate that the element material directions should not be written to the output database. 

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

If this parameter and the EXTERIOR parameter are omitted, output will be written for all the elements in the model.

EXTERIOR

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses. 

Include this parameter to restrict output to only the exterior three-dimensional elements.

If this parameter and the ELSET parameter are omitted, output will be written for all the elements in the model.

POSITION

Set POSITION=CENTROIDAL if values are being written at the centroid of the element (the centroid of the reference surface of a shell element, the midpoint between the end nodes in a beam element). In Abaqus/CFD element output always uses  POSITION=CENTROIDAL.

Set POSITION=INTEGRATION POINTS (default) if values are being written at the integration points at which the variables are actually calculated.

Set POSITION=NODES if the values being written are extrapolated to the nodes of each element in the set but not averaged at the nodes.

### **Optional parameters: **

REBAR

This parameter applies only to rebar in membrane, shell, and surface elements.

This parameter can be used to obtain output only for the rebar in the element set specified; output for the matrix material will not be given. It can be used with or without a value. If it is used without a value, the output will be given for all rebar in the element set. Its value can be set to the name assigned to the rebar on the [*REBAR LAYER](ch17abk12.md) option to specify output for that particular rebar in the element set.

If this parameter is omitted in a model that includes rebar, the output requests govern the output for the matrix material only (except for section forces, when the forces in the rebar are included in the force calculation).

Rebar output can be obtained only in membrane, shell, or surface elements at the integration points and at the centroid of the element.

VARIABLE

Set VARIABLE=ALL to indicate that all element variables applicable to this procedure and material type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default element output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the element variables requested for output must be specified on the data lines.

### **Data lines to request element output: **

**First line (optional, and relevant only if integration point variables are being written for shell, beam, or layered solid elements in an Abaqus/Standard analysis or if integration point variables are being written for shell or beam elements in an Abaqus/Explicit analysis):**

**Second line:**

Repeat the second data line as often as necessary to define the list of variables to be output to the output database.




