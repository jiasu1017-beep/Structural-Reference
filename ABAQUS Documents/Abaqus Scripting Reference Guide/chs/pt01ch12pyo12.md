# 12.12 ConnectorStop object







The ConnectorStop object defines connector stops for one or more components of a connector's relative motion.

The ConnectorStop object is derived from the [ConnectorBehaviorOption](pt01ch12pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.12.1 ConnectorStop(...)

This method creates a connector stop behavior option for a [ConnectorSection](pt01ch46pyo08.md) object.

**Path**

```
mdb.models[*name*].sections[*name*].ConnectorStop
session.odbs[*name*].sections[*name*].ConnectorStop
```

**Required arguments**

None.

**Optional arguments**

*minMotion*

 `None` or a Float specifying the lower bound for the connector's relative position for all specified components, or no lower bound. The default value is `None`.

*maxMotion*

 `None` or a Float specifying the upper bound for the connector's relative position for all specified components, or no upper bound. The default value is `None`.

*components*

A sequence of Ints specifying the components of relative motion for which the behavior is defined.  Possible values are 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The default value is an empty sequence.

**Return value**

A ConnectorStop object.

**Exceptions**

ValueError and TextError.

### 12.12.2 setValues(...)

This method modifies the ConnectorStop object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorStop](pt01ch12pyo12.md#ker-connectorstop-connectorstop-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.12.3 Members

The ConnectorStop object has members with the same names and descriptions as the arguments to the [ConnectorStop](pt01ch12pyo12.md#ker-connectorstop-connectorstop-pyc) method.

### 12.12.4 Corresponding analysis keywords

| [*CONNECTOR STOP](../key/key-link.md#usb-kws-mconnectorstops) |
| --- |




