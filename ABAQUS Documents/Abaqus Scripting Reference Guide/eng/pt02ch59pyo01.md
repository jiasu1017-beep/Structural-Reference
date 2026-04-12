# 59.1 Filter object







The Filter object is the abstract base type for other Filter objects. The Filter object has no explicit constructor. The methods and members of the Filter object are common to all objects derived from the Filter.

**Access**

```
filterApi.filters()[*name*]
```

### 59.1.1 Members

The Filter object has the following members:

**Prototype**

```
odb_String name() const;
double cutoffFrequency() const;
int order() const;
odb_String operation() const;
bool halt() const;
odb_Union limit() const;
odb_String invariant() const;
```

*name*

An odb_String specifying the repository key. This name ANTIALIASING is reserved for filters generated internally by the program.

*cutoffFrequency*

A Double specifying the attenuation point of the filter. Possible values are non-negative numbers.  Order is not available for OperatorFilter.

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




