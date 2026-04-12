# 25.5 ActuatorSensor object







The ActuatorSensor object defines a single point actuator where the actuation is determined by a user subroutine ([`UEL`](../sub/sub-link.md#sub-xsl-uel)). The subroutine senses the data at the same point as the actuator.

The ActuatorSensor object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.5.1 ActuatorSensor(...)

This method creates an ActuatorSensor object.

**Path**

```
mdb.models[*name*].ActuatorSensor
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the actuator/sensor interaction is created. *createStepName* must be set to 'Initial'.

*point*

A [Region](pt01ch45pyo03.md) object specifying the point at which the constraint is applied.

*interactionProperty*

A String specifying the [ActuatorSensorProp](pt01ch25pyo06.md) object associated with this interaction.

*noCoordComponents*

An Int specifying the number of coordinate components supplied to the user subroutine ([`UEL`](../sub/sub-link.md#sub-xsl-uel)).

*unsymm*

A Boolean specifying whether the element matrices are symmetric (ON) or unsymmetric (OFF). The default value is OFF.

*noSolutionDepVar*

An Int specifying the number of solution-dependent variables. The default value is 0.

*userSubUel*

A String specifying the name of the user subroutine ([`UEL`](../sub/sub-link.md#sub-xsl-uel)) that defines the user element.

*dof*

A String specifying the degrees of freedom, separated by commas.

*solutionDepVars*

A sequence of Floats specifying the initial values of the solution-dependent variables.

**Optional arguments**

None.

**Return value**

An ActuatorSensor object.

**Exceptions**

None.

### 25.5.2 setValues(...)

This method modifies the ActuatorSensor object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ActuatorSensor](pt01ch25pyo05.md#ker-actuatorsensor-actuatorsensor-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.5.3 Members

The ActuatorSensor object has members with the same names and descriptions as the arguments to the [ActuatorSensor](pt01ch25pyo05.md#ker-actuatorsensor-actuatorsensor-pyc) method.

### 25.5.4 Corresponding analysis keywords

| [*ELEMENT](../key/key-link.md#usb-kws-melement) |
| --- |
| [*USER ELEMENT](../key/key-link.md#usb-kws-muserelement) |
| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=SOLUTION |




