# *NODE OUTPUT







### *NODE OUTPUTDefine output database requests for nodal data.

This option is used to write nodal variables to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **One of the following mutually exclusive parameters is required when the [*NODE OUTPUT](ch14abk11.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option for Abaqus/Standard or Abaqus/Explicit: **

NSET

Set this parameter equal to the name of the node set for which this output request is being made.

TRACER SET

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the name of the tracer set for which this output request is being made.

### **Optional parameters when the [*NODE OUTPUT](ch14abk11.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), FIELD option: **

EXTERIOR

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses. 

Include this parameter to restrict output to only nodes that belong to the exterior three-dimensional elements.

If this parameter and the NSET parameter are omitted, output will be written for all the nodes in the model.

NSET

Set this parameter equal to the name of the node set for which this output request is being made. 

If this parameter and the EXTERIOR parameter are omitted, output will be written for all the nodes in the model.

TRACER SET

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the name of the tracer set for which this output request is being made. 

This parameter is valid only for displacement output requests.

### **Optional parameter when the [*NODE OUTPUT](ch14abk11.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option: **

GLOBAL

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses. 

This parameter is relevant only at nodes where the [*TRANSFORM](ch19abk11.md) option has been used to define a local coordinate system.

Set GLOBAL=NO to write vector-valued nodal variables in the local directions.

Set GLOBAL=YES (default) to write vector-valued nodal variables in the global directions. This default is the opposite of the default on the [*NODE PRINT](ch14abk12.md) option and is used because most postprocessors assume that components are given in the global system.

### **Optional parameter: **

VARIABLE

Set VARIABLE=ALL to indicate that all nodal variables applicable to this procedure and material type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default nodal output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the nodal variables requested for output must be specified on the data lines.

### **Data lines to request nodal output: **

**First line:**

Repeat this data line as often as necessary to define the nodal variables to be written to the output database.




