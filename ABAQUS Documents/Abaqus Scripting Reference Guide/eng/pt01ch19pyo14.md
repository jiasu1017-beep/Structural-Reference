# 19.14 SpringDashpotToGround object







The SpringDashpotToGround object defines springs and/or dashpots between points and ground on a part or an assembly region.

The SpringDashpotToGround object is derived from the [SpringDashpot](pt01ch19pyo13.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.14.1 SpringDashpotToGround(...)

This method creates a SpringDashpotToGround object.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.SpringDashpotToGround
mdb.models[*name*].rootAssembly.engineeringFeatures\
.SpringDashpotToGround
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the springs and/or dashpots are applied.

*dof*

An Int specifying the degree of freedom associated with the spring and dashpot behaviors.

**Optional arguments**

*orientation*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local directions for the spring and/or dashpot. If *orientation*=`None`, the spring and/or dashpot data are defined in the global coordinate system. The default value is `None`.

*springBehavior*

A Boolean specifying whether to apply spring behavior to the selected points. The default value is OFF.

At least one of the arguments *springBehavior*=ON or *dashpotBehavior*=ON must be specified.

*dashpotBehavior*

A Boolean specifying whether to apply dashpot behavior to the selected points. The default value is OFF.

At least one of the arguments *springBehavior*=ON or *dashpotBehavior*=ON must be specified.

*springStiffness*

A Float specifying the force per relative displacement for the spring. The default value is 0.0.

*dashpotCoefficient*

A Float specifying the force per relative velocity for the dashpot. The default value is 0.0.

**Return value**

A SpringDashpotToGround object.

**Exceptions**

None.

### 19.14.2 setValues(...)

This method modifies the SpringDashpotToGround object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SpringDashpotToGround](pt01ch19pyo14.md#ker-springdashpottoground-springdashpottoground-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.14.3 Members

The SpringDashpotToGround object has members with the same names and descriptions as the arguments to the [SpringDashpotToGround](pt01ch19pyo14.md#ker-springdashpottoground-springdashpottoground-pyc) method.

In addition, the SpringDashpotToGround object has the following member:

*suppressed*

A Boolean specifying whether the spring/dashpot is suppressed or not. The default value is OFF.

### 19.14.4 Corresponding analysis keywords

| [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRING1; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOT1; [*SPRING](../key/key-link.md#usb-kws-mspring); [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |




