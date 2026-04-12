# 3.8 PeriodicAmplitude object







The PeriodicAmplitude object defines an amplitude curve using a Fourier series.

The PeriodicAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.8.1 PeriodicAmplitude(...)

This method creates a PeriodicAmplitude object.

**Path**

```
mdb.models[*name*].PeriodicAmplitude
session.odbs[*name*].PeriodicAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*frequency*

A Float specifying the circular frequency ![](../graphics/ker_eqn00016.gif). Possible values are positive numbers.

*start*

A Float specifying the starting time ![](../graphics/ker_eqn00011.gif). Possible values are positive numbers.

*a_0*

A Float specifying the constant ![](../graphics/ker_eqn00009.gif).

*data*

A sequence of pairs of Floats specifying ![](../graphics/ker_eqn00017.gif) and ![](../graphics/ker_eqn00018.gif) pairs.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A PeriodicAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.8.2 setValues(...)

This method modifies the PeriodicAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PeriodicAmplitude](pt01ch03pyo08.md#ker-periodicamplitude-periodicamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.8.3 Members

The PeriodicAmplitude object has members with the same names and descriptions as the arguments to the [PeriodicAmplitude](pt01ch03pyo08.md#ker-periodicamplitude-periodicamplitude-pyc) method.

### 3.8.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




