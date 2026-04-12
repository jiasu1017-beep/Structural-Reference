# 56.7 PeriodicAmplitude object







The PeriodicAmplitude object defines an amplitude curve using a Fourier series.

The PeriodicAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.7.1 PeriodicAmplitude(...)

This method creates a PeriodicAmplitude object.

**Path**

```
amplitudeApi.PeriodicAmplitude
```

**Prototype**

```
odb_PeriodicAmplitude&
PeriodicAmplitude(const odb_String& name,
                  double frequency,
                  double start,
                  double a_0,
                  const odb_SequenceSequenceDouble& data,
                  const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*frequency*

A Double specifying the circular frequency ![](../graphics/ker_eqn00016.gif). Possible values are positive numbers.

*start*

A Double specifying the starting time ![](../graphics/ker_eqn00011.gif). Possible values are positive numbers.

*a_0*

A Double specifying the constant ![](../graphics/ker_eqn00009.gif).

*data*

An odb_SequenceSequenceDouble specifying ![](../graphics/ker_eqn00017.gif) and ![](../graphics/ker_eqn00018.gif) pairs.

**Optional argument**

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A PeriodicAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.7.2 setValues(...)

This method modifies the PeriodicAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PeriodicAmplitude](pt02ch56pyo07.md#ker-periodicamplitude-periodicamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.7.3 Members

The PeriodicAmplitude object has members with the same names and descriptions as the arguments to the [PeriodicAmplitude](pt02ch56pyo07.md#ker-periodicamplitude-periodicamplitude-cpp) method.

### 56.7.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




