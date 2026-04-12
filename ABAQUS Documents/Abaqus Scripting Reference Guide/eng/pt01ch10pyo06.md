# 10.6 FeFpBehavior object







TheFeFpBehavior               object represents the Hyperelasticity with Permanent Set Behavior type.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.feFpBehavior
```

### 10.6.1 FeFpBehavior(...)

This method creates a FeFpBehavior                     object.

**Path**

```
mdb.models[*name*].calibrations[*name*].behaviors.FeFpBehavior
```

**Required arguments**

*name*

A String specifying the name of the new behavior.

*typeName*

A String specifying the type of the new Behavior. Values can be "ElasIsoBehavior", "ElasPlasIsoBehavior", "FeFpBehavior" or a user plug-in behavior type. For this object it will be "FeFpBehavior"

**Optional arguments**

None.

**Return value**

A FeFpBehavior object.

**Exceptions**

InvalidNameError.

### 10.6.2 setValues(...)

This method modifies the data for an existing FeFpBehavior object.

**Required arguments**

None.

**Optional arguments**

*uniaxialName*

Name of the uniaxial dataset.

*biaxialName*

Name of the biaxial dataset.

*interpolation*

'linear' specifies linear interpolation between data points, otherwise 'logarithmic'.

*uniWeight*

Uniaxial weight factor, uniWeight + biWeight should equal 1.0.

*biWeight*

Biaxial weight factor, uniWeight + biWeight should equal 1.0.

**Return value**

None

**Exceptions**

None.

### 10.6.3 Members

The FeFpBehavior object has members with the same names and descriptions as the arguments to the [FeFpBehavior](pt01ch10pyo06.md#ker-fefpbehavior-fefpbehavior-pyc) method.




