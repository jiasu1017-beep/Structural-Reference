# 56.6 ModulatedAmplitude object







The ModulatedAmplitude object defines a modulated amplitude curve.

The ModulatedAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.6.1 ModulatedAmplitude(...)

This method creates a ModulatedAmplitude object.

**Path**

```
amplitudeApi.ModulatedAmplitude
```

**Prototype**

```
odb_ModulatedAmplitude&
ModulatedAmplitude(const odb_String& name,
                   double initial,
                   double magnitude,
                   double start,
                   double frequency1,
                   double frequency2,
                   const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*initial*

A Double specifying the constant ![](../graphics/ker_eqn00009.gif).

*magnitude*

A Double specifying the coefficient ![](../graphics/ker_eqn00010.gif).

*start*

A Double specifying the starting time ![](../graphics/ker_eqn00011.gif). Possible values are non-negative numbers.

*frequency1*

A Double specifying the circular frequency 1 (![](../graphics/ker_eqn00014.gif)). Possible values are positive numbers.

*frequency2*

A Double specifying the circular frequency 2 (![](../graphics/ker_eqn00015.gif)). Possible values are positive numbers.

**Optional argument**

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A ModulatedAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.6.2 setValues(...)

This method modifies the ModulatedAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ModulatedAmplitude](pt02ch56pyo06.md#ker-modulatedamplitude-modulatedamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.6.3 Members

The ModulatedAmplitude object has members with the same names and descriptions as the arguments to the [ModulatedAmplitude](pt02ch56pyo06.md#ker-modulatedamplitude-modulatedamplitude-cpp) method.

### 56.6.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




