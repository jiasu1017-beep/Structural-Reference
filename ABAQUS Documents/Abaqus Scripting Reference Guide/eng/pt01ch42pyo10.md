# 42.10 KinematicHardening object







 The KinematicHardening object stores the data for initial equivalent plastic strains and, if relevant, the initial backstress tensor.                 

The KinematicHardening object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.10.1 KinematicHardening(...)

 This method creates a KinematicHardening object.                         

**Path**

```
mdb.models[*name*].KinematicHardening
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

**Optional arguments**

*numBackStress*

An Int specifying the number of backstresses. The default value is 1.

*equivPlasticStrain*

A sequence of Floats specifying the initial equivalent plastic strain. 

*backStress*

A sequence of sequences of Floats specifying the initial backstress tensor for kinematic hardening models. The default value is an empty sequence.

*sectPtNum*

A sequence of Ints specifying section point  numbers. This argument is valid only when *definition*=SECTION_PTS.

*definition*

A SymbolicConstant specifying different types of kinematic hardening. Possible values are KINEMATIC_HARDENING, CRUSHABLE_FOAM, REBAR, SECTION_PTS, and USER_DEFINED. The default value is KINEMATIC_HARDENING.

*rebarLayerNames*

A sequence of Strings specifying rebar layer names. This argument is valid only when *definition*=REBAR.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are MAGNITUDE and ANALYTICAL_FIELD. The default value is MAGNITUDE.

**Return value**

A KinematicHardening object.

**Exceptions**

None.

### 42.10.2 setValues(...)

This method modifies the KinematicHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [KinematicHardening](pt01ch42pyo10.md#ker-kinematichardening-kinematichardening-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 42.10.3 Members

The KinematicHardening object has members with the same names and descriptions as the arguments to the [KinematicHardening](pt01ch42pyo10.md#ker-kinematichardening-kinematichardening-pyc) method.

In addition, the KinematicHardening object can have the following member:

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this predefined field. The *field* argument applies only when *distributionType*=ANALYTICAL_FIELD.                                  The default value is an empty string.

### 42.10.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=HARDENING |
| --- |




