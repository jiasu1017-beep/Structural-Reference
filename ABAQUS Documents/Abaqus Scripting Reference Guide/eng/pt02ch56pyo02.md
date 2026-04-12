# 56.2 ActuatorAmplitude object







The ActuatorAmplitude object defines an actuator amplitude curve.

The ActuatorAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.2.1 ActuatorAmplitude(...)

This method creates a ActuatorAmplitude object.

**Path**

```
amplitudeApi.ActuatorAmplitude
```

**Prototype**

```
odb_ActuatorAmplitude&
ActuatorAmplitude(const odb_String& name,
                  const odb_String& timeSpan);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional argument**

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

An ActuatorAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.2.2 setValues(...)

This method modifies the ActuatorAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ActuatorAmplitude](pt02ch56pyo02.md#ker-actuatoramplitude-actuatoramplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.2.3 Members

The ActuatorAmplitude object has members with the same names and descriptions as the arguments to the [ActuatorAmplitude](pt02ch56pyo02.md#ker-actuatoramplitude-actuatoramplitude-cpp) method.

### 56.2.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




