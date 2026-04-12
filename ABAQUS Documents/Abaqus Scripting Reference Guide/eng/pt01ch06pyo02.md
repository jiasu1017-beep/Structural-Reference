# 6.2 ConnectorOrientation object







The ConnectorOrientation object is used to assign a connector orientation to a connector.

**Access**

```
import assembly
mdb.models[*name*].rootAssembly.connectorOrientations[*i*]
import odbAccess
session.odbs[*name*].rootAssembly.connectorOrientations[*i*]
```

### 6.2.1 ConnectorOrientation(...)

This method creates a ConnectorOrientation object.

**Path**

```
mdb.models[*name*].rootAssembly.ConnectorOrientation
session.odbs[*name*].rootAssembly.ConnectorOrientation
```

**Required argument**

*region*

A [Set](pt01ch45pyo04.md) object specifying the region to which the orientation is assigned.

**Optional arguments**

*localCsys1*

A [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the first connector point. This value may be None, indicating the global coordinate system. 

*axis1*

A SymbolicConstant specifying the axis of a datum coordinate system about which an additional rotation is applied. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle1*

A Float specifying the angle of the additional rotation. The default value is 0.0.

*orient2sameAs1*

A Boolean specifying whether or not the second connector point is to use the same local coordinate system, axis, and angle as the first point. The default value is ON.

*localCsys2*

A [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the second connector point. This value may be None, indicating the global coordinate system.

*axis2*

A SymbolicConstant specifying the axis of a datum coordinate system about which an additional rotation is applied. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle2*

A Float specifying the angle of the additional rotation. The default value is 0.0.

**Return value**

A ConnectorOrientation object.

**Exceptions**

None.

### 6.2.2 setValues(...)

This method modifies the ConnectorOrientation object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorOrientation](pt01ch06pyo02.md#ker-connectororientation-connectororientation-pyc) method.

**Return value**

None

**Exceptions**

None.

### 6.2.3 Members

The ConnectorOrientation object has members with the same names and descriptions as the arguments to the [ConnectorOrientation](pt01ch06pyo02.md#ker-connectororientation-connectororientation-pyc) method.




