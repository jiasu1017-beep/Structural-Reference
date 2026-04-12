# 56.12 TabularAmplitude object







The TabularAmplitude object defines an amplitude curve as a table of values at convenient points on the time scale.

The TabularAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.12.1 TabularAmplitude(...)

This method creates a TabularAmplitude object.

**Path**

```
amplitudeApi.TabularAmplitude
```

**Prototype**

```
odb_TabularAmplitude&
TabularAmplitude(const odb_String& name,
                 const odb_SequenceSequenceDouble& data,
                 odb_Union smooth,
                 const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*data*

An odb_SequenceSequenceDouble specifying time/frequency and amplitude pairs. Possible values for time/frequency are positive numbers.

**Optional arguments**

*smooth*

The string "SOLVER_DEFAULT" or a Double specifying the degree of smoothing. Possible float values are between 0 and 0.5.  If *smooth*="SOLVER_DEFAULT", the default degree of smoothing will be determined by the solver. The default value is "SOLVER_DEFAULT".

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A TabularAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.12.2 setValues(...)

This method modifies the TabularAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TabularAmplitude](pt02ch56pyo12.md#ker-tabularamplitude-tabularamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.12.3 Members

The TabularAmplitude object has members with the same names and descriptions as the arguments to the [TabularAmplitude](pt02ch56pyo12.md#ker-tabularamplitude-tabularamplitude-cpp) method.

In addition, the TabularAmplitude object can have the following member:

**Prototype**

```
odb_BaselineCorrection baselineCorrection() const;
```

*baselineCorrection*

A [BaselineCorrection](pt02ch56pyo03.md) object.

### 56.12.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




