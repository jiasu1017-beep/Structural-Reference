# *EL FILE







### *EL FILEDefine results file requests for element variables.

This option is used to select the element variables that will be written to the results (`.fil`) file in an Abaqus/Standard analysis or to the selected results (`.sel`) file in an Abaqus/Explicit analysis. In an Abaqus/Explicit analysis it must be used in conjunction with the [*FILE OUTPUT](ch06abk09.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **References:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **Optional parameters: **

DIRECTIONS

This parameter applies only to Abaqus/Standard analyses.

This parameter is used to obtain the directions of local element or material coordinate systems when component output is requested. The directions are written as a separate record for each point at which a local coordinate system is used. See ["Results file output format," Section 5.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-fformat), for a detailed description.

Set DIRECTIONS=NO (default) if the local coordinate directions should not be written.

Set DIRECTIONS=YES if the local coordinate directions should be written.

ELSET

Set this parameter equal to the name of the element set for which this output request is being made. If this parameter is omitted, the output will be written for all elements in the model. In an Abaqus/Explicit analysis, output will also be written for all of the rebars in the model. The REBAR parameter must be included in an Abaqus/Standard analysis to obtain rebar output.

FREQUENCY

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the output frequency, in increments. The output will always be written to the results file at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

LAST MODE

This parameter applies only to Abaqus/Standard analyses.

This parameter is useful only during eigenvalue extraction for natural frequencies (["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)) and for eigenvalue buckling estimation (["Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling)). Set this parameter equal to the highest mode number for which output is required.

The default value is LAST MODE=*N*, where *N* is the number of modes extracted. If the MODE parameter is used, the default value is LAST MODE=*M*, where *M* is the value of the MODE parameter.

MODE

This parameter applies only to Abaqus/Standard analyses.

This parameter is useful only during eigenvalue extraction for natural frequencies (["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)) and for eigenvalue buckling estimation (["Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling)). Set this parameter equal to the first mode number for which output is required. The default is MODE=1. When performing a [*FREQUENCY](ch06abk35.md) analysis, the normalization will follow the format set by the NORMALIZATION parameter. Otherwise, the normalization is such that the largest displacement component in the mode has a magnitude of 1.0. 

POSITION

This parameter applies only to Abaqus/Standard analyses.

Set POSITION=AVERAGED AT NODES if the values being written are the averages of values extrapolated to the nodes of the elements in the set. Since variables can be discontinuous between elements with different properties, Abaqus/Standard breaks the output into separate tables for different element property definitions within the element set specified. Abaqus/Standard will also output elements of differing types separately. Thus, averaging will occur only over elements that contribute to a node that have the same type.

Set POSITION=CENTROIDAL if values are being written at the centroid of the element (the centroid of the reference surface of a shell element, the midpoint between the end nodes of a beam element).

Set POSITION=INTEGRATION POINTS (default) if values are being written at the integration points at which the variables are actually calculated.

Set POSITION=NODES if the values being written are extrapolated to the nodes of each element in the set but not averaged at the nodes.

REBAR

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used to obtain output only for the rebar in the element set specified; output for the matrix material will not be given. It can be used with or without a value. If it is used without a value, the output will be given for all rebar in the element set. Its value can be set to the name assigned to the rebar on the [*REBAR](ch17abk11.md) option to specify output for that particular rebar in the element set.

If this parameter is omitted in a model that includes rebar, the output requests govern the output for the matrix material only (except for section forces, when the forces in the rebar are included in the force calculation). Rebar output can be obtained only at the integration points in continuum and beam elements. In shell and membrane elements rebar output can be obtained at the integration points and at the centroid of the element.

### **Data lines to request element output in the results file in an Abaqus/Standard analysis: **

**First line (optional, and relevant only if integration point variables are being printed for shell, beam, or layered solid elements):**

**Second line:**

Repeat the second data line as often as necessary to define the list of variables to be output to the results file.

### **Data lines to request element output in the selected results file in an Abaqus/Explicit analysis: **

**First line:**

Repeat this data line as often as necessary to define the list of variables to be output to the selected results file.




