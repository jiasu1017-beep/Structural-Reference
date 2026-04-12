# 12.6 ConnectorFailure object







The ConnectorFailure object defines failure criteria for one or more components of a connector's relative motion.

The ConnectorFailure object is derived from the [ConnectorBehaviorOption](pt01ch12pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.6.1 ConnectorFailure(...)

This method creates a connector failure behavior option for a [ConnectorSection](pt01ch46pyo08.md) object.

**Path**

```
mdb.models[*name*].sections[*name*].ConnectorFailure
session.odbs[*name*].sections[*name*].ConnectorFailure
```

**Required arguments**

None.

**Optional arguments**

*releaseComponent*

The SymbolicConstant ALL or an Int specifying the motion components that fail. If an Int is specified, only that motion component fails when the failure criteria are satisfied. If *releaseComponent*=ALL, all motion components fail. The default value is ALL.

*minMotion*

 `None` or a Float specifying the lower bound for the connector's relative position for all specified components, or no lower bound. The default value is `None`.

*maxMotion*

 `None` or a Float specifying the upper bound for the connector's relative position for all specified components, or no upper bound. The default value is `None`.

*minForce*

 `None` or a Float specifying the lower bound of the force or moment in the directions of the specified components at which locking occurs, or no lower bound. The default value is `None`.

*maxForce*

 `None` or a Float specifying the upper bound of the force or moment in the directions of the specified components at which locking occurs, or no upper bound. The default value is `None`.

*components*

A sequence of Ints specifying the components of relative motion for which the behavior is defined.  Possible values are 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The default value is an empty sequence.

**Return value**

A ConnectorFailure object.

**Exceptions**

ValueError and TextError.

### 12.6.2 setValues(...)

This method modifies the ConnectorFailure object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorFailure](pt01ch12pyo06.md#ker-connectorfailure-connectorfailure-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.6.3 Members

The ConnectorFailure object has members with the same names and descriptions as the arguments to the [ConnectorFailure](pt01ch12pyo06.md#ker-connectorfailure-connectorfailure-pyc) method.

### 12.6.4 Corresponding analysis keywords

| [*CONNECTOR FAILURE](../key/key-link.md#usb-kws-mconnectorfailure) |
| --- |




