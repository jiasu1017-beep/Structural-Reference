# 34.21 OdbRigidBody 对象

刚体对象用于将一组单元和/或一组节点和/或解析曲面与参考节点绑定。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].rigidBodies[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].rigidBodies[*i*]
session.odbs[*name*].rootAssembly.rigidBodies[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.rigidBodies[*i*]
```

### 34.21.1 RigidBody(...)

此方法创建 OdbRigidBody 对象。

**路径**

```
session.odbs[*name*].rootAssembly.instances[*name*].RigidBody
```

```
session.odbs[*name*].rootAssembly.RigidBody
```

**必要参数**

*referenceNode*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定与刚体关联的参考节点集。

**可选参数**

*position*

一个 SymbolicConstant，指定 OdbRigidBody 参考节点相对于刚体其余部分的具体位置。可能的值为 INPUT 和 CENTER_OF_MASS。默认值为 INPUT。

*isothermal*

一个布尔值，指定 OdbRigidBody 是否可以有温度梯度或为等温。这仅用于完全耦合的热应力分析。默认值为 ON。

*elements*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定其运动由刚体参考节点运动控制的元素集。

*tieNodes*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定具有与刚体关联的平移和旋转自由度的节点集。

*pinNodes*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定仅具有与刚体关联的平移自由度的节点集。

*analyticSurface*

一个 [AnalyticSurface](pt01ch34pyo02.md) 对象，指定其运动由刚体参考节点运动控制的解析曲面。

**返回值**

OdbRigidBody 对象。

**异常**

无。

### 34.21.2 成员

OdbRigidBody 对象具有与 [RigidBody](pt01ch34pyo21.md#ker-odbrigidbody-rigidbody-pyc) 方法的参数名称和描述相同的成员。
