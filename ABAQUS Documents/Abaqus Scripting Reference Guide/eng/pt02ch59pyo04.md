# 59.4 Chebyshev2Filter object







The Chebyshev2Filter object defines a Chebyshev type 2 filter.

The Chebyshev2Filter object is derived from the [Filter](pt02ch59pyo01.md) object.

**Access**

```
filterApi.filters()[*name*]
```

### 59.4.1 Chebyshev2Filter(...)

This method creates a Chebyshev2Filter object.

**Path**

```
filterApi.Chebyshev2Filter
```

**Prototype**

```
odb_Chebyshev2Filter&
Chebyshev2Filter(const odb_String& name,
                 double cutoffFrequency,
                 double rippleFactor,
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

*rippleFactor*

A Double specifying the amount of allowable ripple in the filter. Possible values are non-negative numbers less than 1. The default value is 0.025.

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

A Chebyshev2Filter object.

**Exceptions**

InvalidNameError and RangeError.

### 59.4.2 setValues(...)

This method modifies the Chebyshev2Filter object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Chebyshev2Filter](pt02ch59pyo04.md#ker-chebyshev2filter-chebyshev2filter-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 59.4.3 Members

The Chebyshev2Filter object has members with the same names and descriptions as the arguments to the [Chebyshev2Filter](pt02ch59pyo04.md#ker-chebyshev2filter-chebyshev2filter-cpp) method.

### 59.4.4 Corresponding analysis keywords

| [*FILTER](../key/key-link.md#usb-kws-mfilter) |
| --- |




