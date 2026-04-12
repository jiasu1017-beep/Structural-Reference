# 19.15 TwoPointSpringDashpot object







The TwoPointSpringDashpot object defines springs and/or dashpots between two points on a part or an assembly.

The TwoPointSpringDashpot object is derived from the [SpringDashpot](pt01ch19pyo13.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.15.1 TwoPointSpringDashpot(...)

This method creates a TwoPointSpringDashpot object.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.TwoPointSpringDashpot
mdb.models[*name*].rootAssembly.engineeringFeatures\
.TwoPointSpringDashpot
```

**Required arguments**

*name*

A String specifying the repository key.

*regionPairs*

A sequence of pairs of [Region](pt01ch45pyo03.md) objects specifying the points between which the springs and/or dashpots are applied.

*axis*

A SymbolicConstant specifying whether the axis of the springs and/or dashpots follows the rotation of the nodes or is in a specified direction. Possible values are NODAL_LINE and FIXED_DOF.

**Optional arguments**

*dof1*

An Int specifying the degree of freedom with which the springs and/or dashpots are associated at their first points. The *dof1* argument applies only when *axis*=FIXED_DOFS. The default value is 0.

*dof2*

An Int specifying the degree of freedom with which the springs and/or dashpots are associated at their second points. The *dof2* argument applies only when *axis*=FIXED_DOFS.  The default value is 0.

*orientation*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local directions for the spring and/or dashpot. If *orientation*=`None`, the spring and/or dashpot data are defined in the global coordinate system. The default value is `None`.

The *orientation* argument applies only when *axis*=FIXED_DOFS.

*springBehavior*

A Boolean specifying whether to apply spring behavior to the selected point pairs. The default value is OFF.

At least one of the arguments *springBehavior*=ON or *dashpotBehavior*=ON must be specified.

*dashpotBehavior*

A Boolean specifying whether to apply dashpot behavior to the selected point pairs. The default value is OFF.

At least one of the arguments *springBehavior*=ON or *dashpotBehavior*=ON must be specified.

*springStiffness*

A Float specifying the force per relative displacement for the springs. The default value is 0.0.

*dashpotCoefficient*

A Float specifying the force per relative velocity for the dashpots. The default value is 0.0.

**Return value**

A TwoPointSpringDashpot object.

**Exceptions**

None.

### 19.15.2 setValues(...)

This method modifies the TwoPointSpringDashpot object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TwoPointSpringDashpot](pt01ch19pyo15.md#ker-twopointspringdashpot-twopointspringdashpot-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.15.3 Members

The TwoPointSpringDashpot object has members with the same names and descriptions as the arguments to the [TwoPointSpringDashpot](pt01ch19pyo15.md#ker-twopointspringdashpot-twopointspringdashpot-pyc) method.

In addition, the TwoPointSpringDashpot object has the following member:

*suppressed*

A Boolean specifying whether the spring/dashpot is suppressed or not. The default value is OFF.

### 19.15.4 Corresponding analysis keywords

| [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRINGA; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRING2; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOTA; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOT2; [*SPRING](../key/key-link.md#usb-kws-mspring); [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |




