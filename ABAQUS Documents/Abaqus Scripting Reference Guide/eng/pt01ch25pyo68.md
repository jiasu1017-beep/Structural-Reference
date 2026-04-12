# 25.68 StdStabilization object







The StdStabilization object is used in conjunction with [ContactStd](pt01ch25pyo24.md) in Abaqus/Standard analyses to specify contact stabilization.

The StdStabilization object is derived from the [ContactStabilization](pt01ch25pyo23.md) object.

**Access**

```
import interaction
mdb.models[*name*].contactStabilizations[*name*]
```

### 25.68.1 StdStabilization(...)

This method creates a StdStabilization object.

**Path**

```
mdb.models[*name*].StdStabilization
```

**Required argument**

*name*

A String specifying the contact stabilization repository key.

**Optional arguments**

*zeroDistance*

 `None` or a Float specifying the clearance distance at which the stabilization becomes zero. The default value is `None`.

*reductionFactor*

A Float specifying the factor by which the analysis will reduce the contact stabilization coefficient per increment. The default value is 0.1.

*scaleFactor*

A Float specifying the factor by which the analysis will scale the contact stabilization coefficient. The default value is 1.0.

*tangentialFactor*

A Float specifying the factor that scales the contact stabilization coefficient in the tangential direction. The default value is 0.0.

*amplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that defines a time-dependent scale factor for contact stabilization over the step. The default value is an empty string.

*reset*

A Boolean specifying whether to cancel carryover effects from contact stabilization specifications involving nondefault amplitudes that appeared in previous steps. The default value is OFF.

**Return value**

A StdStabilization object.

**Exceptions**

RangeError.

### 25.68.2 setValues(...)

This method modifies the StdStabilization object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [StdStabilization](pt01ch25pyo68.md#ker-stdstabilization-stdstabilization-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 25.68.3 Members

The StdStabilization object has members with the same names and descriptions as the arguments to the [StdStabilization](pt01ch25pyo68.md#ker-stdstabilization-stdstabilization-pyc) method.

### 25.68.4 Corresponding analysis keywords

| [*CONTACT STABILIZATION](../key/key-link.md#usb-kws-hcontactstab) |
| --- |




