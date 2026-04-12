# 61.22 OdbRigidBody 对象

刚体对象用于将一组元素和/或一组节点和/或解析曲面与参考节点绑定。

**访问**

```
odb.parts()[*name*].rigidBodies(*i*)
odb.rootAssembly().instances()[*name*].rigidBodies(*i*)
odb.rootAssembly().rigidBodies(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.rigidBodies(*i*)
```

### 61.22.1 成员

OdbRigidBody 对象可以具有以下成员：

**原型**

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

一个 odb_Enum::odb_PositionEnum，指定 OdbRigidBody 参考节点相对于刚体其余部分的具体位置。可能的值为 odb_Enum::INPUT 和 odb_Enum::CENTER_OF_MASS。默认值为 odb_Enum::INPUT。

*isothermal*

一个 Boolean，指定 OdbRigidBody 是否可以有温度梯度或为等温。这仅用于完全耦合的热应力分析。默认值为 true。

*referenceNode*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定与刚体关联的参考节点集。

*elements*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定其运动由刚体参考节点运动控制的元素集。

*tieNodes*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定具有与刚体关联的平移和旋转自由度 的节点集。

*pinNodes*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定仅有与刚体关联的平移自由度的节点集。

*analyticSurface*

一个 [AnalyticSurface](pt02ch61pyo02.md) 对象，指定其运动由刚体参考节点运动控制的解析曲面。
