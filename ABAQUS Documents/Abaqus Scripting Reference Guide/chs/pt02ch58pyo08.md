# 58.8 ConnectorLock object







The ConnectorLock object defines locking criteria for one or more available components of a connector's relative motion.

The ConnectorLock object is derived from the [ConnectorBehaviorOption](pt02ch58pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*)
```

### 58.8.1 ConnectorLock(...)

This method creates a connector lock behavior option for a [ConnectorSection](pt02ch63pyo08.md).

**Path**

```
sectionApi.sections()[*name*].ConnectorLock
```

**Prototype**

```
odb_ConnectorLock&
ConnectorLock(odb_Union lockingComponent,
              odb_Union minMotion,
              odb_Union maxMotion,
              odb_Union minForce,
              odb_Union maxForce,
              const odb_SequenceInt& components);
```

**Required arguments**

None.

**Optional arguments**

*lockingComponent*

The string "ALL" or an Int specifying the motion components that are locked. If an Int is specified, only that motion component is locked when the locking criteria are satisfied. If *lockingComponent*=ALL, all motion components are locked. The default value is "ALL".

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

A ConnectorLock object.

**Exceptions**

ValueError and TextError.

### 58.8.2 setValues(...)

This method modifies the ConnectorLock object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorLock](pt02ch58pyo08.md#ker-connectorlock-connectorlock-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.8.3 Members

The ConnectorLock object has members with the same names and descriptions as the arguments to the [ConnectorLock](pt02ch58pyo08.md#ker-connectorlock-connectorlock-cpp) method.

### 58.8.4 Corresponding analysis keywords

 [*CONNECTOR LOCK](../key/key-link.md#usb-kws-mconnectorlock) 




