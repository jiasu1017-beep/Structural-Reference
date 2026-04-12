# 34.12 OdbAssembly 对象

OdbAssembly 对象没有构造函数；当创建 [Odb](pt01ch34pyo01.md) 对象时会自动创建它。创建 [Odb](pt01ch34pyo01.md) 对象时，Abaqus 会创建 *rootAssembly* 成员。

**访问**

```
import odbAccess
session.odbs[*name*].rootAssembly
```

### 34.12.1 ConnectorOrientation(...)

此方法为连接器区域分配连接器方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定一个区域。

**可选参数**

*localCsys1*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定第一个连接器节点局部坐标系，或 `None`，表示全局坐标系。

*axis1*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用第一个连接器节点的额外旋转。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle1*

一个 Float，指定围绕第一个连接器节点轴的额外旋转角度。默认值为 0.0。

*orient2sameAs1*

一个布尔值，指定是否为连接器的第二个节点使用相同的方向设置。默认值为 OFF。

*localCsys2*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定第二个连接器节点局部坐标系，或 `None`，表示全局坐标系。

*axis2*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用第二个连接器节点的额外旋转。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle2*

一个 Float，指定围绕第二个连接器节点轴的额外旋转角度。默认值为 0.0。

**返回值**

无

**异常**

如果 *region* 不是元素集：

```
OdbError: Connector orientation assignment requires element set.
```

### 34.12.2 SectionAssignment(...)

此方法用于为实例上的区域分配截面。只能在装配级别分配连接器截面。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定一个区域。

*section*

一个 [Section](pt01ch46pyo01.md) 对象。

**可选参数**

无。

**返回值**

无

**异常**

如果 *region* 不是元素集：

```
OdbError: Section assignment requires element set.
```

### 34.12.3 addElements(...)

此方法用于在使用 OdbAssembly 和/或 [OdbInstance](pt01ch34pyo15.md) 级别定义的节点来定义单元。对于连接到地面的连接器单元，请在连接中指定孤立的节点。地面节点的位置无法指定。这是一个限制。

**警告：**不按标签升序添加单元可能导致 Abaqus/Viewer 错误地绘制等值线。

**必要参数**

*labels*

整数序列，指定单元标签。

*connectivity*

整数序列的序列，指定节点连接性。

*instanceNames*

字符串序列，指定节点连接数组中每个节点的 instanceNames。如果节点在装配级别定义，则实例名称应为空字符串

*type*

一个字符串，指定单元类型。

**可选参数**

*elementSetName*

一个字符串，为此元素集指定名称。默认值为空字符串。

*sectionCategory*

一个 [SectionCategory](pt01ch34pyo27.md) 对象，用于此元素集。

**返回值**

无

**异常**

只有某些单元类型允许在装配级别。例如，连接器单元。

```
OdbError: Addition of this element type is not permitted at the assembly level
```

如果标签数组长度与连接数据长度不匹配：

```
OdbError: Connectivity array must be provided for all element
```

### 34.12.4 addNodes(...)

此方法使用节点标签和坐标向 OdbAssembly 对象添加节点。

**警告：**不按标签升序添加节点可能导致 Abaqus/Viewer 错误地绘制等值线。

**必要参数**

*labels*

整数序列，指定节点标签。

*coordinates*

浮点数序列的序列，指定节点坐标。

**可选参数**

*nodeSetName*

一个字符串，为此节点集指定名称。默认值为 None。

**返回值**

无

**异常**

如果标签长度与坐标长度不匹配：

```
OdbError: Number of node labels and coordinates does not match
```

如果坐标数组宽度与装配维度不匹配：

```
OdbError: Node location specification does not correspond to part dimensions
```

### 34.12.5 RigidBody(...)

此方法在装配上定义一个 [OdbRigidBody](pt01ch34pyo21.md)。

**必要参数**

*referenceNode*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的参考节点。

**可选参数**

*position*

一个符号常量，指定是否由用户定义参考节点的位置。可能的值为 INPUT 和 CENTER_OF_MASS。默认值为 INPUT。

*isothermal*

一个布尔值，指定等温刚体。默认值为 OFF。此参数仅用于完全耦合的热应力分析。

*elset*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的元素集。

*pinNodes*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的销钉型节点。

*tieNodes*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的绑定型节点。

**返回值**

无

**异常**

如果 *referenceNode* 不是节点集：

```
OdbError: Rigid body definition requires a node set.
```

### 34.12.6 成员

OdbAssembly 对象可以具有以下成员：

*instances*

[OdbInstance](pt01ch34pyo15.md) 对象的仓库。

*nodeSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定节点集。

*elementSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定元素集。

*surfaces*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定曲面。

*nodes*

一个 [OdbMeshNodeArray](pt01ch34pyo18.md) 对象。

*elements*

一个 [OdbMeshElementArray](pt01ch34pyo17.md) 对象。

*datumCsyses*

[OdbDatumCsys](pt01ch34pyo13.md) 对象的仓库。

*sectionAssignments*

一个 [SectionAssignmentArray](pt01ch44pyo01.md) 对象。

*rigidBodies*

一个 [OdbRigidBodyArray](pt01ch34pyo21.md) 对象。

*pretensionSections*

一个 [OdbPretensionSectionArray](pt01ch34pyo20.md) 对象。

*connectorOrientations*

一个 [ConnectorOrientationArray](pt01ch06pyo02.md) 对象。
