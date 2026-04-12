# 3.5 DecayAmplitude object







The DecayAmplitude object defines an amplitude curve using an exponential decay.

The DecayAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.5.1 DecayAmplitude(...)

This method creates a DecayAmplitude object.

**Path**

```
mdb.models[*name*].DecayAmplitude
session.odbs[*name*].DecayAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*initial*

A Float specifying the constant ![](../graphics/ker_eqn00009.gif).

*maximum*

A Float specifying the coefficient ![](../graphics/ker_eqn00010.gif).

*start*

A Float specifying the starting time ![](../graphics/ker_eqn00011.gif). Possible values are non-negative numbers.

*decayTime*

A Float specifying the decay time ![](../graphics/ker_eqn00012.gif). Possible values are non-negative numbers.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A DecayAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.5.2 setValues(...)

This method modifies the DecayAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DecayAmplitude](pt01ch03pyo05.md#ker-decayamplitude-decayamplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.5.3 Members

The DecayAmplitude object has members with the same names and descriptions as the arguments to the [DecayAmplitude](pt01ch03pyo05.md#ker-decayamplitude-decayamplitude-pyc) method.

### 3.5.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




