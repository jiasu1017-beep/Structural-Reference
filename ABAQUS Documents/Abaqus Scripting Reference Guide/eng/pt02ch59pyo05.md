# 59.5 OperatorFilter object







The OperatorFilter object defines an operator filter.

The OperatorFilter object is derived from the [Filter](pt02ch59pyo01.md) object.

**Access**

```
filterApi.filters()[*name*]
```

### 59.5.1 OperatorFilter(...)

This method creates an OperatorFilter object.

**Path**

```
filterApi.OperatorFilter
```

**Prototype**

```
odb_OperatorFilter&
OperatorFilter(const odb_String& name,
               double cutoffFrequency,
               int order,
               const odb_String& operation,
               bool halt,
               odb_Union limit,
               const odb_String& invariant);
```

**Required arguments**

*name*

An odb_String specifying the repository key. This name ANTIALIASING is reserved for filters generated internally by the program.

*cutoffFrequency*

A Double specifying the attenuation point of the filter. Possible values are non-negative numbers.  Order is not available for OperatorFilter.

**Optional arguments**

*order*

An Int specifying the highest power of the filter transfer function.  Possible values are non-negative numbers less than or equal to 20.  Order is not available for OperatorFilter. The default value is 2.

*operation*

An odb_String specifying the filter operator. Possible values are "NONE", "MIN", "MAX", and "ABS". The default value is "NONE".

*halt*

A Boolean specifying whether to stop the analysis if the specified limit is reached. The default value is false.

*limit*

The string "NONE" or a Double specifying the threshold limit, an upper or lower bound for output values depending on the operation, or a bound for stopping the analysis when Halt is used. The default value is "NONE".

*invariant*

An odb_String specifying the invariant to which filtering is applied. Possible values are "NONE", "FIRST", and "SECOND". The default value is "NONE".

**Return value**

An OperatorFilter object.

**Exceptions**

InvalidNameError and RangeError.

### 59.5.2 setValues(...)

This method modifies the OperatorFilter object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [OperatorFilter](pt02ch59pyo05.md#ker-operatorfilter-operatorfilter-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 59.5.3 Members

The OperatorFilter object has members with the same names and descriptions as the arguments to the [OperatorFilter](pt02ch59pyo05.md#ker-operatorfilter-operatorfilter-cpp) method.

### 59.5.4 Corresponding analysis keywords

| [*FILTER](../key/key-link.md#usb-kws-mfilter) |
| --- |




