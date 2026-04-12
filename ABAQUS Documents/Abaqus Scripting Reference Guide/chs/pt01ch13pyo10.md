# 13.10 Tie object







The Tie object defines two surfaces to be tied together for the duration of a simulation.

The Tie object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.10.1 Tie(...)

This method creates a Tie object.

**Path**

```
mdb.models[*name*].Tie
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*master*

A [Region](pt01ch45pyo03.md) object specifying the name of the master surface.

*slave*

A [Region](pt01ch45pyo03.md) object specifying the name of the slave surface.

**Optional arguments**

*adjust*

A Boolean specifying whether initial positions of tied slave nodes are adjusted to lie on the master surface. The default value is ON.

*positionToleranceMethod*

A SymbolicConstant specifying the method used to determine the position tolerance. Possible values are COMPUTED and SPECIFIED. The default value is COMPUTED.

*positionTolerance*

A Float specifying the position tolerance. The *positionTolerance* argument applies only when *positionToleranceMethod*=SPECIFIED. The default value is 0.0.

*tieRotations*

A Boolean specifying whether rotation degrees of freedom should be tied. The default value is ON.

*constraintRatioMethod*

A SymbolicConstant specifying the method used to determine the constraint ratio. Possible values are DEFAULT and SPECIFIED. The default value is DEFAULT.

*constraintRatio*

A Float specifying the fractional distance between the master reference surface and the slave node at which the translational constraint should act. The *constraintRatio* argument applies only when *constraintRatioMethod*=SPECIFIED. The default value is 0.0.

*constraintEnforcement*

A SymbolicConstant specifying the discretization method. Possible values are SOLVER_DEFAULT, NODE_TO_SURFACE, and SURFACE_TO_SURFACE. The default value is SOLVER_DEFAULT.

*thickness*

A Boolean specifying whether shell element thickness is considered. The default value is ON.

**Return value**

A Tie object.

**Exceptions**

None.

### 13.10.2 swapSurfaces()

This method switches the master and slave surfaces of a tied constraint. This command is valid only during the step in which the interaction is created.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 13.10.3 setValues(...)

This method modifies the Tie object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Tie](pt01ch13pyo10.md#ker-tie-tie-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 13.10.4 Members

The Tie object has members with the same names and descriptions as the arguments to the [Tie](pt01ch13pyo10.md#ker-tie-tie-pyc) method.

In addition, the Tie object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.10.5 Corresponding analysis keywords

| [*TIE](../key/key-link.md#usb-kws-mtie) |
| --- |




