# 58.12 ConnectorStop object







The ConnectorStop object defines connector stops for one or more components of a connector's relative motion.

The ConnectorStop object is derived from the [ConnectorBehaviorOption](pt02ch58pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*)
```

### 58.12.1 ConnectorStop(...)

This method creates a connector stop behavior option for a [ConnectorSection](pt02ch63pyo08.md) object.

**Path**

```
sectionApi.sections()[*name*].ConnectorStop
```

**Prototype**

```
odb_ConnectorStop&
ConnectorStop(odb_Union minMotion,
              odb_Union maxMotion,
              const odb_SequenceInt& components);
```

**Required arguments**

None.

**Optional arguments**

*minMotion*

The string "NONE" or a Double specifying the lower bound for the connector's relative position for all specified components, or no lower bound. The default value is "NONE".

*maxMotion*

The string "NONE" or a Double specifying the upper bound for the connector's relative position for all specified components, or no upper bound. The default value is "NONE".

*components*

An odb_SequenceInt specifying the components of relative motion for which the behavior is defined.  Possible values are 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The default value is an empty sequence.

**Return value**

A ConnectorStop object.

**Exceptions**

ValueError and TextError.

### 58.12.2 setValues(...)

This method modifies the ConnectorStop object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorStop](pt02ch58pyo12.md#ker-connectorstop-connectorstop-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.12.3 Members

The ConnectorStop object has members with the same names and descriptions as the arguments to the [ConnectorStop](pt02ch58pyo12.md#ker-connectorstop-connectorstop-cpp) method.

### 58.12.4 Corresponding analysis keywords

| [*CONNECTOR STOP](../key/key-link.md#usb-kws-mconnectorstops) |
| --- |




