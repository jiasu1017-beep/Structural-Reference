# 56.11 SpectrumAmplitude object







The SpectrumAmplitude               object defines the spectrum of responses for displacement, velocity, or acceleration to be used in a response spectrum analysis.

The SpectrumAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
Api.amplitudes()[*name*]
```

### 56.11.1 SpectrumAmplitude(...)

This method creates a SpectrumAmplitude                     object.

**Path**

```
Api.SpectrumAmplitude
```

**Prototype**

```
odb_SpectrumAmplitude&
SpectrumAmplitude(const odb_String& name,
                  const odb_String& method,
                  const odb_SequenceSequenceDouble& data,
                  const odb_String& specificationUnits,
                  const odb_String& eventUnits,
                  const odb_String& solution,
                  double timeIncrement,
                  double gravity,
                  bool criticalDamping,
                  const odb_String& timeSpan,
                  const odb_String& amplitude);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*method*

An odb_String specifying the method for specifying the spectrum. Possible values are "DEFINE" and "CALCULATE".

*data*

An odb_SequenceSequenceDouble specifying the magnitude, frequency, and damping values.

**Optional arguments**

*specificationUnits*

An odb_String specifying the units used for specifying the spectrum. Possible values are "DISPLACEMENT", "VELOCITY", "ACCELERATION", and "GRAVITY". The default value is "ACCELERATION".

*eventUnits*

An odb_String specifying the units used to describe the dynamic event in the amplitude used for the calculation. Possible values are "EVENT_DISPLACEMENT", "EVENT_VELOCITY", "EVENT_ACCELERATION", and "EVENT_GRAVITY". The default value is "EVENT_ACCELERATION".

*solution*

An odb_String specifying the solution method for the dynamic equations. Possible values are "ABSOLUTE_VALUE" and "RELATIVE_VALUE". The default value is "ABSOLUTE_VALUE".

*timeIncrement*

A Double specifying the implicit time increment used to calculate the spectrum. This argument is required when the *method*                          = "CALCULATE".                       The default value is 0.0.

*gravity*

A Double specifying the acceleration due to gravity. This argument applies only when *specificationUnits*                          =  "GRAVITY"                          or*eventUnits*                        = "GRAVITY".                       The default value is 1.0.

*criticalDamping*

A Boolean specifying whether to calculate the spectrum for only the specified range of critical damping values or a list of values. If *criticalDamping*                        = true, the spectrum is calculated only for the specified range of critical damping values. If *criticalDamping*                        = false, the spectrum is calculated for a list of damping values.                       The default value is false.

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

*amplitude*

An odb_String specifying the name of the amplitude that describes the dynamic event used to calculate the spectrum. The default value is an empty string.

**Return value**

A SpectrumAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.11.2 setValues(...)

This method modifies the SpectrumAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SpectrumAmplitude](pt02ch56pyo11.md#ker-spectrumamplitude-spectrumamplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.11.3 Members

The SpectrumAmplitude object has members with the same names and descriptions as the arguments to the [SpectrumAmplitude](pt02ch56pyo11.md#ker-spectrumamplitude-spectrumamplitude-cpp) method.

### 56.11.4 Corresponding analysis keywords

| [*SPECTRUM](../key/key-link.md#usb-kws-mspectrum) |
| --- |




