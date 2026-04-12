# 58.6 ConnectorFailure object







The ConnectorFailure object defines failure criteria for one or more components of a connector's relative motion.

The ConnectorFailure object is derived from the [ConnectorBehaviorOption](pt02ch58pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*)
```

### 58.6.1 ConnectorFailure(...)

This method creates a connector failure behavior option for a [ConnectorSection](pt02ch63pyo08.md) object.

**Path**

```
sectionApi.sections()[*name*].ConnectorFailure
```

**Prototype**

```
odb_ConnectorFailure&
ConnectorFailure(odb_Union releaseComponent,
                 odb_Union minMotion,
                 odb_Union maxMotion,
                 odb_Union minForce,
                 odb_Union maxForce,
                 const odb_SequenceInt& components);
```

**Required arguments**

None.

**Optional arguments**

*releaseComponent*

The string "ALL" or an Int specifying the motion components that fail. If an Int is specified, only that motion component fails when the failure criteria are satisfied. If *releaseComponent*="ALL", all motion components fail. The default value is "ALL".

*minMotion*

The string "NONE" or a Double specifying the lower bound for the connector's relative position for all specified components, or no lower bound. The default value is "NONE".

*maxMotion*

The string "NONE" or a Double specifying the upper bound for the connector's relative position for all specified components, or no upper bound. The default value is "NONE".

*minForce*

The string "NONE" or a Double specifying the lower bound of the force or moment in the directions of the specified components at which locking occurs, or no lower bound. The default value is "NONE".

*maxForce*

The string "NONE" or a Double specifying the upper bound of the force or moment in the directions of the specified components at which locking occurs, or no upper bound. The default value is "NONE".

*components*

An odb_SequenceInt specifying the components of relative motion for which the behavior is defined.  Possible values are 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The default value is an empty sequence.

**Return value**

A ConnectorFailure object.

**Exceptions**

ValueError and TextError.

### 58.6.2 setValues(...)

This method modifies the ConnectorFailure object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorFailure](pt02ch58pyo06.md#ker-connectorfailure-connectorfailure-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.6.3 Members

The ConnectorFailure object has members with the same names and descriptions as the arguments to the [ConnectorFailure](pt02ch58pyo06.md#ker-connectorfailure-connectorfailure-cpp) method.

### 58.6.4 Corresponding analysis keywords

| [*CONNECTOR FAILURE](../key/key-link.md#usb-kws-mconnectorfailure) |
| --- |




