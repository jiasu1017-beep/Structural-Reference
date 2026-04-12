# 3.14 UserAmplitude object







The UserAmplitude object defines an amplitude curve using the [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) or [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) user subroutine.

The UserAmplitude object is derived from the [Amplitude](pt01ch03pyo01.md) object.

**Access**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.14.1 UserAmplitude(...)

This method creates a UserAmplitude object.

**Path**

```
mdb.models[*name*].UserAmplitude
session.odbs[*name*].UserAmplitude
```

**Required arguments**

*name*

A String specifying the repository key.

*numVariables*

An Int specifying the number of variables for the [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) or [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) user subroutine.

**Optional argument**

*timeSpan*

A SymbolicConstant specifying the time span of the amplitude. Possible values are STEP and TOTAL. The default value is STEP.

**Return value**

A UserAmplitude object.

**Exceptions**

InvalidNameError and RangeError.

### 3.14.2 setValues(...)

This method modifies the UserAmplitude object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [UserAmplitude](pt01ch03pyo14.md#ker-useramplitude-useramplitude-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 3.14.3 Members

The UserAmplitude object has members with the same names and descriptions as the arguments to the [UserAmplitude](pt01ch03pyo14.md#ker-useramplitude-useramplitude-pyc) method.

### 3.14.4 Corresponding analysis keywords

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |




