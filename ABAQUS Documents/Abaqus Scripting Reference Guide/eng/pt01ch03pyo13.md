# 3.13 TabularAmplitude object







The TabularAmplitude object defines an amplitude curve as a table of values at convenient points on the time scale.

The TabularAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.13.1 TabularAmplitude(...)

This method creates a TabularAmplitude object.

**Path**

```
mdb.models[*name*].TabularAmplitude
session.odbs[*name*].TabularAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*data*

A sequence of pairs of Floats specifying time/frequency and amplitude pairs. Possible values for time/frequency are positive numbers.

**Optional arguments**

*smooth*

The SymbolicConstant SOLVER_DEFAULT or a Float specifying the degree of smoothing. Possible float values are between 0 and 0.5.  If *smooth*=SOLVER_DEFAULT, the default degree of smoothing will be determined by the solver. The default value is SOLVER_DEFAULT.

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A TabularAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.13.2 setValues(...)

This method modifies the TabularAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TabularAmplitude](pt01ch03pyo13.md#ker-tabularamplitude-tabularamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.13.3 Members

The TabularAmplitude object has members with the same names and descriptions as the arguments to the [TabularAmplitude](pt01ch03pyo13.md#ker-tabularamplitude-tabularamplitude-pyc) method.

In addition, the TabularAmplitude object can have the following member:

*baselineCorrection*

A [BaselineCorrection](pt01ch03pyo03.md) object.

### 3.13.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




