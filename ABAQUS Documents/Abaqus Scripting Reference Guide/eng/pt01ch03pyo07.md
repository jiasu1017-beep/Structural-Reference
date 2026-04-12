# 3.7 ModulatedAmplitude object







The ModulatedAmplitude object defines a modulated amplitude curve.

The ModulatedAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.7.1 ModulatedAmplitude(...)

This method creates a ModulatedAmplitude object.

**Path**

```
mdb.models[*name*].ModulatedAmplitude
session.odbs[*name*].ModulatedAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*initial*

A Float specifying the constant ![](../graphics/ker_eqn00009.gif).

*magnitude*

A Float specifying the coefficient ![](../graphics/ker_eqn00010.gif).

*start*

A Float specifying the starting time ![](../graphics/ker_eqn00011.gif). Possible values are non-negative numbers.

*frequency1*

A Float specifying the circular frequency 1 (![](../graphics/ker_eqn00014.gif)). Possible values are positive numbers.

*frequency2*

A Float specifying the circular frequency 2 (![](../graphics/ker_eqn00015.gif)). Possible values are positive numbers.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A ModulatedAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.7.2 setValues(...)

This method modifies the ModulatedAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ModulatedAmplitude](pt01ch03pyo07.md#ker-modulatedamplitude-modulatedamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.7.3 Members

The ModulatedAmplitude object has members with the same names and descriptions as the arguments to the [ModulatedAmplitude](pt01ch03pyo07.md#ker-modulatedamplitude-modulatedamplitude-pyc) method.

### 3.7.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




