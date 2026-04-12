# 3.10 SmoothStepAmplitude object







The SmoothStepAmplitude object defines an amplitude that ramps up or down smoothly from one data point to another.

The SmoothStepAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.10.1 SmoothStepAmplitude(...)

This method creates a SmoothStepAmplitude object.

**Path**

```
mdb.models[*name*].SmoothStepAmplitude
session.odbs[*name*].SmoothStepAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*data*

A sequence of pairs of Floats specifying time/frequency and amplitude pairs. Possible values for time/frequency are positive numbers.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A SmoothStepAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.10.2 setValues(...)

This method modifies the SmoothStepAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SmoothStepAmplitude](pt01ch03pyo10.md#ker-smoothstepamplitude-smoothstepamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.10.3 Members

The SmoothStepAmplitude object has members with the same names and descriptions as the arguments to the [SmoothStepAmplitude](pt01ch03pyo10.md#ker-smoothstepamplitude-smoothstepamplitude-pyc) method.

### 3.10.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




