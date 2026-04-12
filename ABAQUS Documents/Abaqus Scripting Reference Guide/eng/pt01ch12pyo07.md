# 12.7 ConnectorFriction object







The ConnectorFriction object defines Coulomb-like or hysteretic friction behavior for one or more components of a connector's relative motion.

The ConnectorFriction object is derived from the [ConnectorBehaviorOption](pt01ch12pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.7.1 ConnectorFriction(...)

This method creates a connector friction behavior option for a [ConnectorSection](pt01ch46pyo08.md) object.  Depending upon the arguments provided, the friction behavior can be Coulomb-like or hysteretic in nature.

**Path**

```
mdb.models[*name*].sections[*name*].ConnectorFriction
session.odbs[*name*].sections[*name*].ConnectorFriction
```

**Required arguments**

None.

**Optional arguments**

*frictionModel*

A SymbolicConstant specifying the desired frictional response model. Possible values are PREDEFINED and USER_CUSTOMIZED. The default value is PREDEFINED.

*slipStyle*

A SymbolicConstant specifying the method of indicating the slip direction: either specified or computed based upon the force potential data. Possible values are SPECIFY and COMPUTE. The default value is SPECIFY.

This argument is applicable only if *frictionModel*=USER_CUSTOMIZED.

*tangentDirection*

 `None` or an Int specifying the direction for which the frictional behavior is specified. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *tangentDirection* ![](../graphics/ker_eqn00013.gif) 6, indicating an available component of relative motion. This argument applies only if *frictionModel*=USER_CUSTOMIZED and if *slipStyle*=SPECIFY. The default value is `None`.

*stickStiffness*

 `None` or a Float specifying the stick stiffness associated with the frictional behavior in the direction specified by *tangentDirection*. If this argument is omitted, Abaqus computes an appropriate number for the stick stiffness. The default value is `None`.

*componentType*

A SymbolicConstant specifying the type of the *independentComponents*. Possible values are POSITION, MOTION, and NO_INDEPENDENT_COMPONENTS. The default value is NO_INDEPENDENT_COMPONENTS.

*slipDependency*

A Boolean specifying whether the table data depend on accumulated slip. The default value is OFF.

This argument applies only if *frictionModel*=USER_CUSTOMIZED.

*temperatureDependency*

A Boolean specifying whether the table data depend on temperature. The default value is OFF.

This argument applies only if *frictionModel*=USER_CUSTOMIZED.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

This argument applies only if *frictionModel*=USER_CUSTOMIZED.

*useContactForceComponent*

A Boolean specifying whether the contact force component will be defined. The default value is OFF.

This argument applies only if *frictionModel*=USER_CUSTOMIZED.

*contactForceStyle*

A SymbolicConstant specifying the method of indicating the contact force component direction: either specified or computed based on upon a DerivedComponent. Possible values are COMPONENT_NUMBER and DERIVED_COMPONENT. The default value is COMPONENT_NUMBER.

This argument is applicable only if *frictionModel*=USER_CUSTOMIZED and if *useContactForceComponent*=ON.

*contactForceComponent*

An Int specifying the contact force component direction. This argument applies only if *frictionModel*=USER_CUSTOMIZED,  if *useContactForceComponent*=ON, and if *contactForceStyle*=COMPONENT_NUMBER. The default value is 0.

*forcePotentialOperator*

A SymbolicConstant specifying the contribution operator for the force potential contributions. Possible values are SUM and MAXIMUM. The default value is SUM.

This argument is applicable only if *frictionModel*=USER_CUSTOMIZED and if *slipStyle*=COMPUTE.

*forcePotentialExponent*

A Float specifying the number equal to the inverse of the overall exponent in the force potential definition. The default value is 2.0.

This argument is applicable only if *frictionModel*=USER_CUSTOMIZED, if *slipStyle*=COMPUTE, and if *forcePotentialOperator*=SUM.

*connectorPotentials*

A [ConnectorPotentialArray](pt01ch12pyo11.md) object specifying one [ConnectorPotential](pt01ch12pyo11.md) object for each force potential contribution.                             This member can be specified only if *frictionModel*=USER_CUSTOMIZED, and if *slipStyle*=COMPUTE.

*table*

A sequence of sequences of Floats specifying friction properties. The default value is an empty sequence.

If *frictionModel*=PREDEFINED, each sequence of the table data specifies: 
- If applicable, the first geometric scaling constant relevant to frictional interactions.
- Etc., up to as many geometric scaling constants as are associated with this connection type.
- Internal contact force/moment generating friction in the first predefined slip direction.
- If applicable, internal contact force/moment generating friction in the second predefined slip direction.
- Connector constitutive relative motion in the direction specified by *independentComponent*.
- Accumulated slip in the first predefined slip direction, if the data depend on accumulated slip.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *frictionModel*=USER_CUSTOMIZED, each sequence of the table data specifies: 
- Effective radius of the cylindrical or spherical surface over which frictional slip occurs in the connector associated with frictional effects in the direction specified by *tangentDirection*. This radius is relevant only if the connection type includes an available rotational component of relative motion and *tangentDirection*=SLIP_DIRECTION.
- Internal contact force/moment generating friction in the direction specified by *tangentDirection*.
- Connector constitutive relative motion in the direction specified by *independentComponent*.
- Accumulated slip in the direction specified by *tangentDirection*, if the data depend on accumulated slip.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

*independentComponents*

A sequence of Ints specifying the independent components.  Possible values are 1 ![](../graphics/ker_eqn00013.gif) *independentComponents* ![](../graphics/ker_eqn00013.gif) 6. In addition, each independent component value must be unique. The *independentComponents* argument applies only if *frictionModel*=USER_CUSTOMIZED. Only available components can be specified. The default value is an empty sequence.

**Return value**

A ConnectorFriction object.

**Exceptions**

ValueError and TextError.

### 12.7.2 setValues(...)

This method modifies the ConnectorFriction object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorFriction](pt01ch12pyo07.md#ker-connectorfriction-connectorfriction-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.7.3 Members

The ConnectorFriction object has members with the same names and descriptions as the arguments to the [ConnectorFriction](pt01ch12pyo07.md#ker-connectorfriction-connectorfriction-pyc) method.

In addition, the ConnectorFriction object can have the following members:

*tangentialBehavior*

A [TangentialBehavior](pt01ch12pyo14.md) object.

*derivedComponent*

A [DerivedComponent](pt01ch12pyo13.md) object specifying the [DerivedComponent](pt01ch12pyo13.md) used to compute the contact force component direction. This argument applies only if *frictionModel*=USER_CUSTOMIZED,  if *useContactForceComponent*=ON, and if *contactForceStyle*=DERIVED_COMPONENT.

*options*

A [ConnectorOptions](pt01ch12pyo09.md) object specifying the [ConnectorOptions](pt01ch12pyo09.md) used         to define tabular options for this [ConnectorBehaviorOption](pt01ch12pyo01.md).

### 12.7.4 Corresponding analysis keywords

| [*CONNECTOR FRICTION](../key/key-link.md#usb-kws-mconnectorfriction), [*FRICTION](../key/key-link.md#usb-kws-hfriction), [*CONNECTOR POTENTIAL](../key/key-link.md#usb-kws-mconnectorpotential), [*CONNECTOR DERIVED COMPONENT](../key/key-link.md#usb-kws-mconnectorderivedcomp) |
| --- |




