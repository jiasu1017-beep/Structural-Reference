# 3.6 EquallySpacedAmplitude object







The EquallySpacedAmplitude object defines a list of amplitude values at fixed time intervals beginning at a specified value of time.

The EquallySpacedAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.6.1 EquallySpacedAmplitude(...)

This method creates an EquallySpacedAmplitude object.

**Path**

```
mdb.models[*name*].EquallySpacedAmplitude
session.odbs[*name*].EquallySpacedAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*fixedInterval*

A Float specifying the fixed time interval at which the amplitude data are given. Possible values are positive numbers.

*data*

A sequence of Floats specifying the amplitude values.

**Optional arguments**

*begin*

A Float specifying the time at which the first amplitude data are given. Possible values are non-negative numbers. The default value is 0.0.

*smooth*

The SymbolicConstant SOLVER_DEFAULT or a Float specifying the degree of smoothing. Possible float values are 0 ![](../graphics/ker_eqn00013.gif) *smoothing* ![](../graphics/ker_eqn00013.gif) 0.5. If *smooth*=SOLVER_DEFAULT, the default degree of smoothing will be determined by the solver. The default value is SOLVER_DEFAULT.

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

An EquallySpacedAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.6.2 setValues(...)

This method modifies the EquallySpacedAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [EquallySpacedAmplitude](pt01ch03pyo06.md#ker-equallyspacedamplitude-equallyspacedamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.6.3 Members

The EquallySpacedAmplitude object has members with the same names and descriptions as the arguments to the [EquallySpacedAmplitude](pt01ch03pyo06.md#ker-equallyspacedamplitude-equallyspacedamplitude-pyc) method.

In addition, the EquallySpacedAmplitude object can have the following member:

*baselineCorrection*

A [BaselineCorrection](pt01ch03pyo03.md) object.

### 3.6.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




