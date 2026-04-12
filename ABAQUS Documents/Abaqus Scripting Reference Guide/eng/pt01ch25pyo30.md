# 25.30 ExpContactControl object







The ExpContactControl object is used in Abaqus/Explicit analyses to specify optional solution controls for problems involving contact between bodies.

The ExpContactControl object is derived from the [ContactControl](pt01ch25pyo16.md) object.

**Access**

```
import interaction
mdb.models[*name*].contactControls[*name*]
```

### 25.30.1 ExpContactControl(...)

This method creates an ExpContactControl object.

**Path**

```
mdb.models[*name*].ExpContactControl
```

**Required argument**

*name*

A String specifying the contact controls repository key.

**Optional arguments**

*globTrkChoice*

A SymbolicConstant specifying whether or not the default value will be used for the maximum number of increments between global contact searches. Possible values are DEFAULT and SPECIFY. The default value is DEFAULT.

*globTrkInc*

An Int specifying the maximum number of increments between global contact searches. The *globTrkInc* argument applies only when *globTrkChoice*=SPECIFY. The default value is 100 for surface-to-surface contact and 4 for self-contact.

*fastLocalTrk*

A Boolean specifying whether to use the more computationally efficient local tracking method. The default value is ON.

*scalePenalty*

A Float specifying the factor by which Abaqus/Explicit will scale the default penalty stiffness to obtain the stiffnesses used for the penalty contact pairs. The default value is 1.0.

*warpCheckPeriod*

An Int specifying the number of increments between checks for highly warped facets on master surfaces. The default value is 20.

*warpCutoff*

A Float specifying the out-of-plane warping angle (in degrees), at which a facet will be considered  to be highly warped. The default value is 20.0.

**Return value**

An ExpContactControl object.

**Exceptions**

RangeError.

### 25.30.2 setValues(...)

This method modifies the ExpContactControl object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ExpContactControl](pt01ch25pyo30.md#ker-expcontactcontrol-expcontactcontrol-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 25.30.3 Members

The ExpContactControl object has members with the same names and descriptions as the arguments to the [ExpContactControl](pt01ch25pyo30.md#ker-expcontactcontrol-expcontactcontrol-pyc) method.

### 25.30.4 Corresponding analysis keywords

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |




