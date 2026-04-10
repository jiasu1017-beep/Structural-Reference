# *FILTER







### *FILTERDefine a filter and/or operator for output filtering and/or operating.

This option defines a digital filter and/or an operator to be used in conjunction with the [*OUTPUT](ch15abk03.md) option. It can be used to pre-filter and/or operate on the output as the analysis progresses.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Filter toolset

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this filter and/or operator.

### **Optional parameters: **

HALT

Include this parameter if you want the analysis to stop when the value specified with the  LIMIT parameter is reached. 

This parameter must be used in conjunction with the  LIMIT parameter.

INVARIANT

This parameter can be used only in conjunction with the  OPERATOR parameter to indicate that you want to filter and/or operate on the invariant of the element or nodal output field variable. 

Set INVARIANT=FIRST to apply the filtering to the first invariant. 

Set INVARIANT=SECOND to apply the filtering to the second invariant.

Set INVARIANT=MAXP to apply the filtering to the maximum principal stress.

Set INVARIANT=INTERMP to apply the filtering to the intermediate principal stress.

Set INVARIANT=MINP to apply the filtering to the minimum principal stress.

See ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput), for more information.

LIMIT

Include this parameter if you want to set a limit (cap value) to the output variables. 

This parameter must be used in conjunction with the OPERATOR parameter.

OPERATOR

This parameter can be used with or without the TYPE parameter. When it is used with a filter type, it will operate on filtered data; and when it is used without a filter type, it will operate on raw (unfiltered) data.

Set OPERATOR=MAX if you want to obtain the maximum value for the variables for which this filter is used. You can put a cap value on the maximum value by using the  LIMIT parameter.

Set OPERATOR=MIN if you want to obtain the minimum value for the variables for which this filter is used. You can put a cap value on the minimum value by using the  LIMIT parameter.

Set OPERATOR=ABSMAX if you want to obtain the absolute maximum value for the variables for which this filter is used. You can put a cap value on this value by using the  LIMIT parameter.

START CONDITION

This parameter must be used with the TYPE parameter.

Set START CONDITION=DC (default) to pre-charge the filter with constant values equal to the first raw data value.

Set START CONDITION=USER DEFINED to pre-charge the filter with constant values equal to the user-defined value.

TYPE

Set TYPE=BUTTERWORTH (which is the default value when OPERATOR is omitted) to define a Butterworth filter.

Set TYPE=CHEBYS1 to define a Type I Chebyshev filter.

Set TYPE=CHEBYS2 to define a Type II Chebyshev filter.

### **Data lines to define a Butterworth filter: **

**First line:**

**Second line (only needed if START CONDITION=USER DEFINED):**

### **Data lines to define a Type I Chebyshev filter: **

**First line:**

**Second line (only needed if START CONDITION=USER DEFINED):**

### **Data lines to define a Type II Chebyshev filter: **

**First line:**

**Second line (only needed if START CONDITION=USER DEFINED):**




