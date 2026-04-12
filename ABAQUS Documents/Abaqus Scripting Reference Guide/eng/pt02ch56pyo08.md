# 56.8 PsdDefinition object







The PsdDefinition               object defines the cross-spectral density frequency function for random response loading.

The PsdDefinition object is derived from the [Amplitude](pt02ch56pyo01.md) object.

**Access**

```
Api.amplitudes()[*name*]
```

### 56.8.1 PsdDefinition(...)

This method creates a PsdDefinition                     object.

**Path**

```
Api.PsdDefinition
```

**Prototype**

```
odb_PsdDefinition&
PsdDefinition(const odb_String& name,
              const odb_SequenceSequenceDouble& data,
              const odb_String& unitType,
              double referenceGravityAcceleration,
              double referenecePower,
              bool user,
              const odb_String& timeSpan,
              const odb_String& amplitude);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*data*

An odb_SequenceSequenceDouble specifying the real part of the frequency function, the imaginary part of the frequency function, and the frequency or frequency band number values, depending on the value of *unitType*.

**Optional arguments**

*unitType*

An odb_String specifying the type of units for specifying the frequency function.  "FORCE" implies power units.  "BASE" implies gravity used to define base motion.  "DB" implies decibel units. Possible values are "FORCE", "BASE", and "DB". The default value is "FORCE".

*referenceGravityAcceleration*

A Double specifying the reference gravity acceleration. This argument applies when *unitType*                          = "BASE".                       The default value is 1.0.

*referenecePower*

A Double specifying the reference power value, in load units squared.  This argument applies when *unitType*                          =  "DB".                       The default value is 0.0.

*user*

A Boolean specifying whether the frequency function is defined in user subroutine UPSD.  If specified, then *data* is not applicable, and the *unitType* value must not be "DB".                       The default value is false.

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".

*amplitude*

An odb_String specifying the name of the amplitude that describes the dynamic event used to define the cross-spectral density frequency function. The default value is an empty string.

**Return value**

A PsdDefinition object.

**Exceptions**

InvalidNameError and RangeError.

### 56.8.2 setValues(...)

This method modifies the PsdDefinition object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PsdDefinition](pt02ch56pyo08.md#ker-psddefinition-psddefinition-cpp) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 56.8.3 Members

The PsdDefinition object has members with the same names and descriptions as the arguments to the [PsdDefinition](pt02ch56pyo08.md#ker-psddefinition-psddefinition-cpp) method.

### 56.8.4 Corresponding analysis keywords

| [*PSD-DEFINITION](../key/key-link.md#usb-kws-mpsddef) |
| --- |




