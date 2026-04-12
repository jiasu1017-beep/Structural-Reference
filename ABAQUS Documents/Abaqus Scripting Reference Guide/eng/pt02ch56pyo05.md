# 56.5 EquallySpacedAmplitude object







The EquallySpacedAmplitude object defines a list of amplitude values at fixed time intervals beginning at a specified value of time.

The EquallySpacedAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.5.1 EquallySpacedAmplitude(...)

This method creates an EquallySpacedAmplitude object.

**Path**

```
amplitudeApi.EquallySpacedAmplitude
```

**Prototype**

```
odb_EquallySpacedAmplitude&
EquallySpacedAmplitude(const odb_String& name,
                       double fixedInterval,
                       const odb_SequenceDouble& data,
                       double begin,
                       odb_Union smooth,
                       const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*fixedInterval*

A Double specifying the fixed time interval at which the amplitude data are given. Possible values are positive numbers.

*data*

An odb_SequenceDouble specifying the amplitude values.

**Optional arguments**

*begin*

A Double specifying the time at which the first amplitude data are given. Possible values are non-negative numbers. The default value is 0.0.

*smooth*

The string "SOLVER_DEFAULT" or a Double specifying the degree of smoothing. Possible float values are 0 ![](../graphics/ker_eqn00013.gif) *smoothing* ![](../graphics/ker_eqn00013.gif) 0.5. If *smooth*="SOLVER_DEFAULT", the default degree of smoothing will be determined by the solver. The default value is "SOLVER_DEFAULT".

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

An EquallySpacedAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.5.2 setValues(...)

This method modifies the EquallySpacedAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [EquallySpacedAmplitude](pt02ch56pyo05.md#ker-equallyspacedamplitude-equallyspacedamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.5.3 Members

The EquallySpacedAmplitude object has members with the same names and descriptions as the arguments to the [EquallySpacedAmplitude](pt02ch56pyo05.md#ker-equallyspacedamplitude-equallyspacedamplitude-cpp) method.

In addition, the EquallySpacedAmplitude object can have the following member:

**Prototype**

```
odb_BaselineCorrection baselineCorrection() const;
```

*baselineCorrection*

A [BaselineCorrection](pt02ch56pyo03.md) object.

### 56.5.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




