# 3.2 ActuatorAmplitude object







The ActuatorAmplitude object defines an actuator amplitude curve.

The ActuatorAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.2.1 ActuatorAmplitude(...)

This method creates a ActuatorAmplitude object.

**Path**

```
mdb.models[*name*].ActuatorAmplitude
session.odbs[*name*].ActuatorAmplitude
```

**Required argument**

*name*

A String specifying the repository key.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

An ActuatorAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.2.2 setValues(...)

This method modifies the ActuatorAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ActuatorAmplitude](pt01ch03pyo02.md#ker-actuatoramplitude-actuatoramplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.2.3 Members

The ActuatorAmplitude object has members with the same names and descriptions as the arguments to the [ActuatorAmplitude](pt01ch03pyo02.md#ker-actuatoramplitude-actuatoramplitude-pyc) method.

### 3.2.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




