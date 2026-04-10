# *CONTACT OUTPUT







### *CONTACT OUTPUTSpecify contact variables to be written to the output database.

This option is used to write contact variables to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **One of the following mutually exclusive parameters is required when the [*CONTACT OUTPUT](ch03abk67.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option in an Abaqus/Explicit analysis: **

CPSET

Set this parameter equal to the name of the contact pair set for which this output request is being made.

NSET

Set this parameter equal to the name of the node set for which this output request is being made. This parameter is valid only for nodes defined under [*BOND](ch02abk11.md), and only the BONDSTAT and BONDLOAD output variables may be requested.

SURFACE

Set this parameter equal to the name of the surface in the general contact domain for which this output request is being made.

### **Optional parameter when the SURFACE parameter is included: **

SECOND SURFACE

This parameter is used to write contact output limited to a pair of contact surfaces. Set this parameter equal to the name of the second surface in the general contact domain that along with the first surface specified by the SURFACE parameter identifies the pair of contact surfaces.

### **Optional parameters when the [*CONTACT OUTPUT](ch03abk67.md) option is used in conjunction with the [*OUTPUT](ch15abk03.md), FIELD option in an Abaqus/Explicit analysis: **

CPSET

Set this parameter equal to the name of the contact pair set for which this output request is being made. If this parameter and the GENERAL CONTACT parameter are omitted, the output will be written for all of the contact pairs in the model and the general contact domain (if it has been defined).

GENERAL CONTACT

Include this parameter to request output for the general contact domain. If this parameter and the CPSET parameter are omitted, the output will be written for all of the contact pairs in the model and the general contact domain (if it has been defined).

SURFACE

Set this parameter equal to the name of the surface in the general contact domain for which this output request is being made.

### **Optional parameter when the SURFACE parameter is included: **

SECOND SURFACE

This parameter is used to write contact output limited to a pair of contact surfaces. Set this parameter equal to the name of the second surface in the general contact domain that along with the first surface specified by the SURFACE parameter identifies the pair of contact surfaces.

### **Optional parameter in Abaqus/Explicit analyses: **

VARIABLE

Set VARIABLE=ALL to indicate that all contact variables applicable to this procedure should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default contact output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the contact variables requested for output must be specified on the data lines.

### **Optional parameters in Abaqus/Standard analyses: **

MASTER

Set this parameter equal to the name of a master surface of one or more contact pairs for which this request is being made. Specifying this parameter eliminates output for general contact associated with this request, regardless of whether or not this surface participates in general contact.

NSET

Set this parameter equal to the name of the node set for which this output request is being made.

SLAVE

Set this parameter equal to the name of a slave surface of one or more contact pairs for which this request is being made. Specifying this parameter eliminates output for general contact associated with this request, regardless of whether or not this surface participates in general contact.

SURFACE

Set this parameter equal to the name of the surface containing facets of cracked enriched elements for which this request is being made. This parameter is valid only for small sliding contact between cracked surfaces in enriched elements.

VARIABLE

Set VARIABLE=ALL to indicate that all contact variables applicable to this procedure should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default contact output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the contact variables requested for output must be specified on the data lines.

### **Data lines to request contact output: **

**First line:**

Repeat this data line as often as necessary to define the list of variables to be written to the output database.




