# *OUTPUT







### *OUTPUTDefine output requests to the output database.

This option is used to write contact, element, energy, nodal, or diagnostic output to the output database. In an Abaqus/Standard analysis it is also used to write modal or radiation output to the output database. In an Abaqus/Explicit analysis it is also used to write incrementation output to the output database. The [*CONTACT OUTPUT](ch03abk67.md), [*ELEMENT OUTPUT](ch05abk10.md), [*ENERGY OUTPUT](ch05abk23.md), [*INCREMENTATION OUTPUT](ch09abk15.md), [*MODAL OUTPUT](ch13abk20.md), [*NODE OUTPUT](ch14abk11.md), and/or [*RADIATION OUTPUT](ch17abk03.md) options can be used in conjunction with this option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Standard output variable identifiers," Section 4.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-houtputvar)
- ["Abaqus/Explicit output variable identifiers," Section 4.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-hfileoutputvar)
- ["Abaqus/CFD output variable identifiers," Section 4.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-hcfdoutputvar)
- ["Overview of job diagnostics," Section 41.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-out-overview)
- [*CONTACT OUTPUT](ch03abk67.md)
- [*ELEMENT OUTPUT](ch05abk10.md)
- [*ENERGY OUTPUT](ch05abk23.md)
- [*INCREMENTATION OUTPUT](ch09abk15.md)
- [*MODAL OUTPUT](ch13abk20.md)
- [*NODE OUTPUT](ch14abk11.md)
- [*RADIATION OUTPUT](ch17abk03.md)
- [*TIME POINTS](ch19abk07.md)

### Defining output requests in an Abaqus/Standard analysis

### **One of the following mutually exclusive parameters is required: **

DIAGNOSTICS

Set DIAGNOSTICS=YES (default) to indicate that detailed diagnostic information should be written to the output database. Set DIAGNOSTICS=NO to suppress the output.

FIELD

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as field-type output.

HISTORY

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as history-type output.

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written to the output database at the last increment of each step. Set FREQUENCY=0 to suppress the output.

If this parameter and the NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are omitted, output will be written at every increment of the analysis for all procedure types except [*DYNAMIC](ch04abk43.md) and [*MODAL DYNAMIC](ch13abk18.md); output will be written every 10 increments for these procedure types.

The FREQUENCY, NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are mutually exclusive.

MODE LIST

Include this parameter to indicate that a list of eigenmodes for which output is desired will be listed on the data lines. This parameter is valid only in a [*FREQUENCY](ch06abk35.md), [*COMPLEX FREQUENCY](ch03abk26.md), or [*BUCKLE](ch02abk16.md) procedure, and  if the FIELD parameter is included.

NAME

Set this parameter equal to the name associated with this output definition.

NUMBER INTERVAL

Set this parameter equal to the number of intervals during the step at which the output database states are to be written.

If this parameter and the FREQUENCY, TIME INTERVAL, and TIME POINTS parameters are omitted, output will be written at every increment of the analysis for all procedure types except [*DYNAMIC](ch04abk43.md) and [*MODAL DYNAMIC](ch13abk18.md); output will be written every 10 increments for these procedure types.

The FREQUENCY, NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are mutually exclusive.

TIME MARKS

Set TIME MARKS=YES (default) to write results at the exact times dictated by the NUMBER INTERVAL, TIME INTERVAL, or TIME POINTS parameter.

Set TIME MARKS=NO to write results to the output database at the increment ending immediately after the time dictated by the NUMBER INTERVAL, TIME INTERVAL, or TIME POINTS parameter.

TIME POINTS

Set this parameter equal to the name of the [*TIME POINTS](ch19abk07.md) option that defines the time points at which output is to be written.

If this parameter and the FREQUENCY, NUMBER INTERVAL, and TIME INTERVAL parameters are omitted, output will be written at every increment of the analysis for all procedure types except [*DYNAMIC](ch04abk43.md) and [*MODAL DYNAMIC](ch13abk18.md); output will be written every 10 increments for these procedure types.

The FREQUENCY, NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are mutually exclusive.

### **The following parameters are optional and valid only if the FIELD or HISTORY parameter is included: **

OP

Set OP=NEW (default) to indicate that all output database requests defined in previous steps should be removed. New output database requests can be defined.

Set OP=ADD to indicate that the output request being defined should be added to the output requests defined in previous steps.

Set OP=REPLACE to indicate that this output request should replace an output request of the same type (e.g., FIELD) and frequency defined in a previous step. If there is no matching request, this output request will be interpreted as OP=ADD.

TIME INTERVAL

Set this parameter equal to the time interval at which the output states are to be written.

If this parameter and the FREQUENCY, NUMBER INTERVAL, and TIME POINTS parameters are omitted, output will be written at every increment of the analysis for all procedure types except [*DYNAMIC](ch04abk43.md) and [*MODAL DYNAMIC](ch13abk18.md); output will be written every 10 increments for these procedure types.

The FREQUENCY, NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are mutually exclusive.

VARIABLE

Set VARIABLE=ALL to indicate that all variables applicable to this procedure and material type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default output variables for the current procedure type should be written to the output database. Additional output requests can be defined with the output options used in conjunction with the [*OUTPUT](ch15abk03.md) option, listed previously. Preselected output is ignored in SIM-based dynamic analysis procedures.

If this parameter is omitted, only the variables requested for output with the individual output options will be written to the output database.

The output behavior of the variables included in ALL or PRESELECT cannot be controlled by the parameters or data lines of the individual output options. To get the desired output behavior of a particular variable in an individual output option, the particular variable must be listed in that individual output option.

### **The following parameter is optional and valid only if the HISTORY parameter is included: **

SENSOR

Include this parameter to associate this history output request with a sensor definition. The name of the associated sensor is given by the NAME parameter. 

### **Data lines to list desired eigenmodes if the MODE LIST parameter is included: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### Defining output requests in an Abaqus/Explicit analysis

### **One of the following mutually exclusive parameters is required: **

DIAGNOSTICS

Set DIAGNOSTICS=YES (default) to indicate that detailed diagnostic information should be written to the output database. Set DIAGNOSTICS=NO to suppress the output.

FIELD

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as field-type output.

HISTORY

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as history-type output.

### **Optional parameter: **

NAME

Set this parameter equal to the name associated with this output definition.

### **The following parameters are optional and valid only if the FIELD parameter is included: **

NUMBER INTERVAL

Set this parameter equal to the number of intervals during the step at which the output database states are to be written. Abaqus/Explicit will always write the results at the beginning of the step. For example, if NUMBER INTERVAL=10, Abaqus/Explicit will write 11 output database states consisting of the values at the beginning of the step and the values at the end of 10 intervals throughout the step. The value of this parameter must be a positive integer or zero. A value of zero suppresses all output. If this parameter is omitted, its value will be set to 20.

The NUMBER INTERVAL and TIME POINTS parameters are mutually exclusive.

TIME MARKS

Set TIME MARKS=NO (default) to write results to the output database at the increment ending immediately after the time dictated by the NUMBER INTERVAL or TIME POINTS parameter.

Set TIME MARKS=YES to write results at the exact times dictated by the NUMBER INTERVAL or TIME POINTS parameter.

TIME MARKS=YES cannot be used when either the FIXED TIME INCREMENTATION or DIRECT USER CONTROL parameter is included on the [*DYNAMIC](ch04abk43.md) option.

TIME POINTS

Set this parameter equal to the name of the [*TIME POINTS](ch19abk07.md) option that defines the time points at which output is to be written. If this parameter and the NUMBER INTERVAL parameter are omitted, field output will be written at 20 equally spaced intervals throughout the step.

The NUMBER INTERVAL and TIME POINTS parameters are mutually exclusive.

### **The following parameters are optional and valid only if the HISTORY parameter is included: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written to the output database at the last increment of each step. Set FREQUENCY=0 to suppress the output. If both this parameter and the TIME INTERVAL parameter are omitted, history output will be written at 200 equally spaced intervals throughout the step.

The FREQUENCY and TIME INTERVAL parameters are mutually exclusive.

SENSOR

Include this parameter to associate this history output request with a sensor definition. The name of the associated sensor is given by the NAME parameter. 

### **The following parameters are optional and valid only if the FIELD or HISTORY parameter is included: **

FILTER

Set this parameter equal to the name of the [*FILTER](ch06abk12.md) option to be used to filter the element and nodal field output or the element, nodal, contact, fastener interaction, or integrated history output.

Set FILTER=ANTIALIASING to filter the data based on the time interval that is specified; in this case the filter does not need to be defined in the model data. The antialiasing filter cannot be used with the FREQUENCY parameter for history output.

OP

Set OP=NEW (default) to indicate that all output database requests defined in previous steps should be removed. New output database requests can be defined.

Set OP=ADD to indicate that the output request being defined should be added to the output requests defined in previous steps.

Set OP=REPLACE to indicate that this output request should replace an output request of the same type (e.g., FIELD) and frequency defined in a previous step. If there is no matching request, this output request will be interpreted as OP=ADD.

TIME INTERVAL

Set this parameter equal to the time interval at which the output states are to be written.

For field output Abaqus/Explicit will always write the output at the beginning of the step. If both this parameter and the NUMBER INTERVAL parameter are omitted, field output will be written at 20 equally spaced intervals throughout the step. The NUMBER INTERVAL, TIME INTERVAL, and TIME POINTS parameters are mutually exclusive for field data.

For history output Abaqus/Explicit will always write the data values at the beginning and end of the step. If both this parameter and the FREQUENCY parameter are omitted, history output will be written at 200 equally spaced intervals throughout the step. The FREQUENCY and TIME INTERVAL parameters are mutually exclusive for history data.

VARIABLE

Set VARIABLE=ALL to indicate that all variables applicable to this procedure and material type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default output variables for the current procedure type should be written to the output database. Additional output requests can be defined with the output options used in conjunction with the [*OUTPUT](ch15abk03.md) option, listed previously. 

If this parameter is omitted, only the variables requested for output with the individual output options will be written to the output database.

The output behavior of the variables included in ALL or PRESELECT cannot be controlled by the parameters or data lines of the individual output options. To get the desired output behavior of a particular variable in an individual output option, the particular variable must be listed in that individual output option.

### **There are no data lines associated with this option in Abaqus/Explicit. **

### Defining output requests in an Abaqus/CFD analysis

### **One of the following mutually exclusive parameters is required: **

FIELD

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as field-type output. Abaqus/CFD will always write field output at the beginning and end of a step.

HISTORY

Include this parameter to indicate that the output requests used in conjunction with the [*OUTPUT](ch15abk03.md) option will be written to the output database as history-type output. Abaqus/CFD will always write history output at the beginning and end of a step.

### **Optional parameters: **

NAME

Set this parameter equal to the name associated with this output definition.

FREQUENCY

Set this parameter equal to the output frequency, in increments. Set FREQUENCY=0 to suppress the output. If this parameter, the NUMBER INTERVAL and the TIME INTERVAL parameters are omitted, field output will be written at 20 equally spaced intervals, and history output at 200 equally spaced intervals.

The FREQUENCY, NUMBER INTERVAL, and TIME INTERVAL parameters are mutually exclusive.

NUMBER INTERVAL

Set this parameter equal to the number of intervals during the step at which the output database states are to be written. Set NUMBER INTERVAL=0 to suppress the output.

The FREQUENCY, NUMBER INTERVAL, and TIME INTERVAL parameters are mutually exclusive.

TIME INTERVAL

Set this parameter equal to the time interval at which the output states are to be written.

The FREQUENCY, NUMBER INTERVAL, and TIME INTERVAL parameters are mutually exclusive.

OP

Set OP=NEW (default) to indicate that all output database requests defined in previous steps should be removed. New output database requests can be defined.

Set OP=ADD to indicate that the output request being defined should be added to the output requests defined in previous steps.

Set OP=REPLACE to indicate that this output request should replace an output request of the same type (e.g., FIELD) and output clock (e.g., FREQUENCY) defined in a previous step. If there is no matching request, this output request will be interpreted as OP=ADD.

### **There are no data lines associated with this option in Abaqus/CFD. **




