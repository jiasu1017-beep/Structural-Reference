# 56.10 SolutionDependentAmplitude object







The SolutionDependentAmplitude object defines a solution-dependent amplitude for superplastic forming analysis.

The SolutionDependentAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.10.1 SolutionDependentAmplitude(...)

This method creates a SolutionDependentAmplitude object.

**Path**

```
amplitudeApi.SolutionDependentAmplitude
```

**Prototype**

```
odb_SolutionDependentAmplitude&
SolutionDependentAmplitude(const odb_String& name,
                           double initial,
                           double minimum,
                           double maximum,
                           const odb_String& timeSpan);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional arguments**

*initial*

A Double specifying the initial amplitude value. Possible values are those between *minimum* and *maximum*. The default value is 1.0.

*minimum*

A Double specifying the minimum amplitude value. Possible values are those smaller than *maximum* and *initial*. The default value is 0.1.

*maximum*

A Double specifying the maximum amplitude value. Possible values are those larger than *minimum* and *initial*. The default value is 1000.0.

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A SolutionDependentAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.10.2 setValues(...)

This method modifies the SolutionDependentAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SolutionDependentAmplitude](pt02ch56pyo10.md#ker-solutiondependentamplitude-solutiondependentamplitud-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.10.3 Members

The SolutionDependentAmplitude object has members with the same names and descriptions as the arguments to the [SolutionDependentAmplitude](pt02ch56pyo10.md#ker-solutiondependentamplitude-solutiondependentamplitud-cpp) method.

### 56.10.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




