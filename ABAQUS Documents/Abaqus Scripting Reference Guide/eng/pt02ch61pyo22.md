# 61.22 OdbRigidBody object







The Rigid body object is used to bind a set of elements and/or a set of nodes and/or an analytical surface with a reference node.

**Access**

```
odb.parts()[*name*].rigidBodies(*i*)
odb.rootAssembly().instances()[*name*].rigidBodies(*i*)
odb.rootAssembly().rigidBodies(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.rigidBodies(*i*)
```

### 61.22.1 Members

The OdbRigidBody object can have the following members:

**Prototype**

```
odb_Enum::odb_PositionEnum position() const;
bool isothermal() const;
odb_Set referenceNode() const;
odb_Set elements() const;
odb_Set tieNodes() const;
odb_Set pinNodes() const;
odb_AnalyticSurface analyticSurface() const;
```

*position*

An odb_Enum::odb_PositionEnum specifying the specific location of the OdbRigidBody reference node relative to the rest of the rigid body. Possible values are odb_Enum::INPUT and odb_Enum::CENTER_OF_MASS. The default value is odb_Enum::INPUT.

*isothermal*

A Boolean specifying specify whether the OdbRigidBody can have temperature gradients or be isothermal. This is used             only for fully coupled thermal-stress analysis The default value is true.

*referenceNode*

An [OdbSet](pt02ch61pyo24.md) object specifying the reference node set associated with the rigid body.

*elements*

An [OdbSet](pt02ch61pyo24.md) object specifying the element set whose motion is governed by the motion of rigid body reference node.

*tieNodes*

An [OdbSet](pt02ch61pyo24.md) object specifying the node set which have both translational and rotational degrees of freedom associated with the rigid body.

*pinNodes*

An [OdbSet](pt02ch61pyo24.md) object specifying the node set which have only translational degrees of freedom associated with the rigid body.

*analyticSurface*

An [AnalyticSurface](pt02ch61pyo02.md) object specifying the analytic surface whose motion is governed by the motion of rigid body reference node.




