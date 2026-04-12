# 22.4 Chebyshev2Filter object







The Chebyshev2Filter object defines a Chebyshev type 2 filter.

The Chebyshev2Filter object is derived from the [Filter](pt01ch22pyo01.md) object.

**Access**

```
import filter
mdb.models[*name*].filters[*name*]
import odbFilter
session.odbs[*name*].filters[*name*]
```

### 22.4.1 Chebyshev2Filter(...)

This method creates a Chebyshev2Filter object.

**Path**

```
mdb.models[*name*].Chebyshev2Filter
session.odbs[*name*].Chebyshev2Filter
```

**Required arguments**

*name*

A String specifying the repository key. This name ANTIALIASING is reserved for filters generated internally by the program.

*cutoffFrequency*

A Float specifying the attenuation point of the filter. Possible values are non-negative numbers.  Order is not available for OperatorFilter.

**Optional arguments**

*rippleFactor*

A Float specifying the amount of allowable ripple in the filter. Possible values are non-negative numbers less than 1. The default value is 0.025.

*order*

An Int specifying the highest power of the filter transfer function.  Possible values are non-negative numbers less than or equal to 20.  Order is not available for OperatorFilter. The default value is 2.

*operation*

A SymbolicConstant specifying the filter operator. Possible values are NONE, MIN, MAX, and ABS. The default value is NONE.

*halt*

A Boolean specifying whether to stop the analysis if the specified limit is reached. The default value is OFF.

*limit*

 `None` or a Float specifying the threshold limit, an upper or lower bound for output values depending on the operation, or a bound for stopping the analysis when Halt is used. The default value is `None`.

*invariant*

A SymbolicConstant specifying the invariant to which filtering is applied. Possible values are NONE, FIRST, and SECOND. The default value is NONE.

**Return value**

A Chebyshev2Filter object.

**Exceptions**

InvalidNameError and RangeError.

### 22.4.2 setValues(...)

This method modifies the Chebyshev2Filter object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Chebyshev2Filter](pt01ch22pyo04.md#ker-chebyshev2filter-chebyshev2filter-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 22.4.3 Members

The Chebyshev2Filter object has members with the same names and descriptions as the arguments to the [Chebyshev2Filter](pt01ch22pyo04.md#ker-chebyshev2filter-chebyshev2filter-pyc) method.

### 22.4.4 Corresponding analysis keywords

| [*FILTER](../key/key-link.md#usb-kws-mfilter) |
| --- |




