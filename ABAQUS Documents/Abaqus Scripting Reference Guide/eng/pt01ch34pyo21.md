# 34.21 OdbRigidBody object







The Rigid body object is used to bind a set of elements and/or a set of nodes and/or an analytical surface with a reference node.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].rigidBodies[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].rigidBodies[*i*]
session.odbs[*name*].rootAssembly.rigidBodies[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.rigidBodies[*i*]
```

### 34.21.1 RigidBody(...)

This method creates a OdbRigidBody object.

**Path**

```
session.odbs[*name*].rootAssembly.instances[*name*].RigidBody
```

```
session.odbs[*name*].rootAssembly.RigidBody
```

**Required argument**

*referenceNode*

An [OdbSet](pt01ch34pyo23.md) object specifying the reference node set associated with the rigid body.

**Optional arguments**

*position*

A SymbolicConstant specifying the specific location of the OdbRigidBody reference node relative to the rest of the rigid body. Possible values are INPUT and CENTER_OF_MASS. The default value is INPUT.

*isothermal*

A Boolean specifying specify whether the OdbRigidBody can have temperature gradients or be isothermal. This is used             only for fully coupled thermal-stress analysis The default value is ON.

*elements*

An [OdbSet](pt01ch34pyo23.md) object specifying the element set whose motion is governed by the motion of rigid body reference node.

*tieNodes*

An [OdbSet](pt01ch34pyo23.md) object specifying the node set which have both translational and rotational degrees of freedom associated with the rigid body.

*pinNodes*

An [OdbSet](pt01ch34pyo23.md) object specifying the node set which have only translational degrees of freedom associated with the rigid body.

*analyticSurface*

An [AnalyticSurface](pt01ch34pyo02.md) object specifying the analytic surface whose motion is governed by the motion of rigid body reference node.

**Return value**

An OdbRigidBody object.

**Exceptions**

None.

### 34.21.2 Members

The OdbRigidBody object has members with the same names and descriptions as the arguments to the [RigidBody](pt01ch34pyo21.md#ker-odbrigidbody-rigidbody-pyc) method.




