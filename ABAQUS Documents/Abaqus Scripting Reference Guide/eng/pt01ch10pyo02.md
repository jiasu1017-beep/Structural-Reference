# 10.2 Behavior object







The Behavior               object specifies the method used for calibrating a material.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors
```

### 10.2.1 Behavior(...)

This method creates a Behavior                     object.

**Path**

```
mdb.models[*name*].calibrations[*name*].Behavior
```

**Required arguments**

*name*

A String specifying the name of the new behavior.

*typeName*

A String specifying the type of the new Behavior. Values can be "ElasIsoBehavior", "ElasPlasIsoBehavior", "FeFpBehavior", or a user plug-in behavior type.

**Optional arguments**

None.

**Return value**

A Behavior object.

**Exceptions**

InvalidNameError.

### 10.2.2 Members

The Behavior object has members with the same names and descriptions as the arguments to the [Behavior](pt01ch10pyo02.md#ker-behavior-behavior-pyc) method.

In addition, the Behavior object can have the following members:

*elasIsoBehavior*

An [ElasIsoBehavior](pt01ch10pyo04.md) object.

*feFpBehavior*

A [FeFpBehavior](pt01ch10pyo06.md) object.

*elasPlasIsoBehavior*

An [ElasPlasIsoBehavior](pt01ch10pyo05.md) object.




