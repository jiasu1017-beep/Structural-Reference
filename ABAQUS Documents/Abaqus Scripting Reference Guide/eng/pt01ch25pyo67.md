# 25.67 StdInitialization object







The StdInitialization object is used in conjunction with [ContactStd](pt01ch25pyo24.md) in Abaqus/Standard analyses to specify contact initialization data.

The StdInitialization object is derived from the [ContactInitialization](pt01ch25pyo20.md) object.

**Access**

```
import interaction
mdb.models[*name*].contactInitializations[*name*]
```

### 25.67.1 StdInitialization(...)

This method creates a StdInitialization object.

**Path**

```
mdb.models[*name*].StdInitialization
```

**Required argument**

*name*

A String specifying the contact initialization repository key.

**Optional arguments**

*overclosureType*

A SymbolicConstant specifying the type of overclosure to be defined. Possible values are ADJUST, INTERFERENCE, and CLEARANCE. The default value is ADJUST.

*interferenceDistance*

 `None` or a Float specifying the interference distance.  This argument is valid only when *overclosureType*=INTERFERENCE. The default value is `None`.

*clearanceDistance*

 `None` or a Float specifying the initial clearance distance.  This argument is valid only when *overclosureType*=CLEARANCE, and must be specified in that case. The default value is `None`.

*openingTolerance*

 `None` or a Float specifying the distance tolerance within which initial openings will undergo strain-free adjustments.  This argument is not valid when *overclosureType*=INTERFERENCE unless a value has been specified for *interferenceDistance*. The default value is `None`.

*overclosureTolerance*

 `None` or a Float specifying the distance tolerance within which initial overclosures will undergo strain-free adjustments.. The default value is `None`.

**Return value**

A StdInitialization object.

**Exceptions**

RangeError.

### 25.67.2 setValues(...)

This method modifies the StdInitialization object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [StdInitialization](pt01ch25pyo67.md#ker-stdinitialization-stdinitialization-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 25.67.3 Members

The StdInitialization object has members with the same names and descriptions as the arguments to the [StdInitialization](pt01ch25pyo67.md#ker-stdinitialization-stdinitialization-pyc) method.

### 25.67.4 Corresponding analysis keywords

| [*CONTACT INITIALIZATION DATA](../key/key-link.md#usb-kws-hcontactinitdata) |
| --- |




