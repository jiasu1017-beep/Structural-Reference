# 56.13 UserAmplitude object







The UserAmplitude object defines an amplitude curve using the [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) or [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) user subroutine.

The UserAmplitude object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.13.1 UserAmplitude(...)

This method creates a UserAmplitude object.

**Path**

```
amplitudeApi.UserAmplitude
```

**Prototype**

```
odb_UserAmplitude&
UserAmplitude(const odb_String& name,
              int numVariables,
              const odb_String& timeSpan);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*numVariables*

An Int specifying the number of variables for the [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) or [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) user subroutine.

**Optional argument**

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

**Return value**

A UserAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 56.13.2 setValues(...)

This method modifies the UserAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [UserAmplitude](pt02ch56pyo13.md#ker-useramplitude-useramplitude-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.13.3 Members

The UserAmplitude object has members with the same names and descriptions as the arguments to the [UserAmplitude](pt02ch56pyo13.md#ker-useramplitude-useramplitude-cpp) method.

### 56.13.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




