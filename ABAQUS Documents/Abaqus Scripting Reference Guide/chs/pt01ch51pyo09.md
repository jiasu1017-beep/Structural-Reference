# 51.9 TimePoint object







The TimePoint object defines time points at which data are written to the output database or restart files.

**Access**

```
import step
mdb.models[*name*].timePoints[*name*]
```

### 51.9.1 TimePoint(...)

This method creates a TimePoint object.

**Path**

```
mdb.models[*name*].TimePoint
```

**Required arguments**

*name*

A String specifying the repository key.

*points*

A sequence of sequences of Floats specifying time points at which data are written to the output database or restart files.

**Optional arguments**

None.

**Return value**

A TimePoint object.

**Exceptions**

InvalidNameError and RangeError.

### 51.9.2 setValues(...)

This method modifies the TimePoint object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TimePoint](pt01ch51pyo09.md#ker-timepoint-timepoint-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 51.9.3 Members

The TimePoint object has members with the same names and descriptions as the arguments to the [TimePoint](pt01ch51pyo09.md#ker-timepoint-timepoint-pyc) method.

### 51.9.4 Corresponding analysis keywords

| [*TIME POINTS](../key/key-link.md#usb-kws-htimepoints) |
| --- |




