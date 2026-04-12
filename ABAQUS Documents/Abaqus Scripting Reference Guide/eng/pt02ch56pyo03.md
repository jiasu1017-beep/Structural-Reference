# 56.3 BaselineCorrection object







The BaselineCorrection object modifies an acceleration history to minimize the overall drift of the displacement obtained from the time integration of the given acceleration.

**Access**

```
amplitudeApi.amplitudes()[*name*].baselineCorrection()
```

### 56.3.1 BaselineCorrection(...)

This method creates a BaselineCorrection object.

**Path**

```
amplitudeApi.amplitudes()[*name*].BaselineCorrection
```

**Prototype**

```
odb_BaselineCorrection&
BaselineCorrection(const odb_SequenceDouble& intervals);
```

**Required arguments**

None.

**Optional argument**

*intervals*

An odb_SequenceDouble specifying the correction time interval end points. Possible values are positive and monotonically increasing Floats. The default value is an empty sequence.

**Return value**

A BaselineCorrection object.

**Exceptions**

RangeError.

### 56.3.2 setValues(...)

This method modifies the BaselineCorrection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BaselineCorrection](pt02ch56pyo03.md#ker-baselinecorrection-baselinecorrection-cpp) method.

**Return value**

None

**Exceptions**

RangeError.

### 56.3.3 Members

The BaselineCorrection object has members with the same names and descriptions as the arguments to the [BaselineCorrection](pt02ch56pyo03.md#ker-baselinecorrection-baselinecorrection-cpp) method.

### 56.3.4 Corresponding analysis keywords

| [*BASELINE CORRECTION](../key/key-link.md#usb-kws-mbasecorrection) |
| --- |




