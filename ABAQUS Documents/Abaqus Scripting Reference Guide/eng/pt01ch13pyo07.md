# 13.7 MultipointConstraint object







The MultipointConstraint object defines a constraint between a group of MultipointConstraint nodes located on a region and a reference point.

The MultipointConstraint object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.7.1 MultipointConstraint(...)

This method creates a MultipointConstraint object.

**Path**

```
mdb.models[*name*].MultipointConstraint
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface on which the MultipointConstraint nodes are located.

*controlPoint*

A [Region](pt01ch45pyo03.md) object specifying the constraint control point.

*mpcType*

A SymbolicConstant specifying the MPC type of the constraint. Possible values are BEAM_MPC, ELBOW_MPC, PIN_MPC, LINK_MPC, TIE_MPC, and USER_MPC.

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the initial orientation of the local coordinate system for the MultipointConstraint's degrees of freedom. If *localCsys*=`None`, the MultipointConstraint is defined in the global coordinate system. The default value is `None`.

*userType*

An Int specifying to differentiate between different constraint types in a user-defined MultipointConstraint. The default value is 0.

The *userType* argument applies only when *mpcType*=USER_MPC.

*userMode*

A SymbolicConstant specifying the mode of the constraint when it is user-defined. Possible values are DOF_MODE_MPC and NODE_MODE_MPC. The default value is DOF_MODE_MPC.

The *userMode* argument applies only when *mpcType*=USER_MPC.

**Return value**

A MultipointConstraint object.

**Exceptions**

None.

### 13.7.2 setValues(...)

This method modifies the MultipointConstraint object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MultipointConstraint](pt01ch13pyo07.md#ker-multipointconstraint-multipointconstraint-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 13.7.3 Members

The MultipointConstraint object has members with the same names and descriptions as the arguments to the [MultipointConstraint](pt01ch13pyo07.md#ker-multipointconstraint-multipointconstraint-pyc) method.

In addition, the MultipointConstraint object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.7.4 Corresponding analysis keywords

| [*MPC](../key/key-link.md#usb-kws-mmpc) |
| --- |




