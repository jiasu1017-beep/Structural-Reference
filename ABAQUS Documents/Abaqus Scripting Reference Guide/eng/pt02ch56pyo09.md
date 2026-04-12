# 56.9 SmoothStepAmplitude object







The SmoothStepAmplitude object defines an amplitude that ramps up or down smoothly from one data point to another.

The SmoothStepAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.9.1 SmoothStepAmplitude(...)

This method creates a SmoothStepAmplitude object.

**Path**

```
amplitudeApi.SmoothStepAmplitude
```

**Prototype**

```
odb_SmoothStepAmplitude&
SmoothStepAmplitude(const odb_String& name,
                    const odb_SequenceSequenceDouble& data,
                    const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*data*

An odb_SequenceSequenceDouble specifying time/frequency and amplitude pairs. Possible values for time/frequency are positive numbers.

**Optional argument**

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A SmoothStepAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.9.2 setValues(...)

This method modifies the SmoothStepAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SmoothStepAmplitude](pt02ch56pyo09.md#ker-smoothstepamplitude-smoothstepamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.9.3 Members

The SmoothStepAmplitude object has members with the same names and descriptions as the arguments to the [SmoothStepAmplitude](pt02ch56pyo09.md#ker-smoothstepamplitude-smoothstepamplitude-cpp) method.

### 56.9.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




