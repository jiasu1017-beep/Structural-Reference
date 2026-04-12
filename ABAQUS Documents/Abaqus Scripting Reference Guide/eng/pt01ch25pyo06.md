# 25.6 ActuatorSensorProp object







The ActuatorSensorProp object is an interaction property that defines the properties referred to by an [ActuatorSensor](pt01ch25pyo05.md) object.

The ActuatorSensorProp object is derived from the [InteractionProperty](pt01ch25pyo48.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.6.1 ActuatorSensorProp(...)

This method creates an ActuatorSensorProp object.

**Path**

```
mdb.models[*name*].ActuatorSensorProp
```

**Required argument**

*name*

A String specifying the interaction property repository key.

**Optional arguments**

*realProperties*

A sequence of Floats specifying the `PROPS` array used by user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel). The default value is an empty sequence.

*integerProperties*

A sequence of Ints specifying the `JPROPS` array used by user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel). The default value is an empty sequence.

**Return value**

An ActuatorSensorProp object.

**Exceptions**

None.

### 25.6.2 setValues(...)

This method modifies the ActuatorSensorProp object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ActuatorSensorProp](pt01ch25pyo06.md#ker-actuatorsensorprop-actuatorsensorprop-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 25.6.3 Members

The ActuatorSensorProp object has members with the same names and descriptions as the arguments to the [ActuatorSensorProp](pt01ch25pyo06.md#ker-actuatorsensorprop-actuatorsensorprop-pyc) method.

### 25.6.4 Corresponding analysis keywords

| [*UEL PROPERTY](../key/key-link.md#usb-kws-muelproperty) |
| --- |




