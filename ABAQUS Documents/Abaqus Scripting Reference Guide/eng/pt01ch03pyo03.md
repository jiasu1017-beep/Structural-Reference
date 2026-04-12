# 3.3 BaselineCorrection object







The BaselineCorrection object modifies an acceleration history to minimize the overall drift of the displacement obtained from the time integration of the given acceleration.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*].baselineCorrection
import odbAmplitude
session.odbs[*name*].amplitudes[*name*].baselineCorrection
```

### 3.3.1 BaselineCorrection(...)

This method creates a BaselineCorrection object.

**Path**

```
mdb.models[*name*].amplitudes[*name*].BaselineCorrection
session.odbs[*name*].amplitudes[*name*].BaselineCorrection
```

**Required arguments**

None.

**Optional argument**

*intervals*

A sequence of Floats specifying the correction time interval end points. Possible values are positive and monotonically increasing Floats. The default value is an empty sequence.

**Return value**

A BaselineCorrection object.

**Exceptions**

RangeError.

### 3.3.2 setValues(...)

This method modifies the BaselineCorrection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BaselineCorrection](pt01ch03pyo03.md#ker-baselinecorrection-baselinecorrection-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 3.3.3 Members

The BaselineCorrection object has members with the same names and descriptions as the arguments to the [BaselineCorrection](pt01ch03pyo03.md#ker-baselinecorrection-baselinecorrection-pyc) method.

### 3.3.4 Corresponding analysis keywords

| [*BASELINE CORRECTION](../key/key-link.md#usb-kws-mbasecorrection) |
| --- |




