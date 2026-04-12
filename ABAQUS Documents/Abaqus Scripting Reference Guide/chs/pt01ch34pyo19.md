# 34.19 OdbPart 对象

OdbPart 对象类似于内核 Part 对象，包含节点和单元，但不包含几何。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*]
```

### 34.19.1 Part(...)

此方法创建 OdbPart 对象。节点和单元在稍后阶段添加到此对象。

**路径**

```
session.odbs[*name*].Part
```

**必要参数**

*name*

一个字符串，指定部件名称。

*embeddedSpace*

一个 SymbolicConstant，指定 [Part](pt01ch37pyo01.md) 对象的维度。可能的值为 THREE_D、TWO_D_PLANAR 和 AXISYMMETRIC。

*type*

一个 SymbolicConstant，指定 [Part](pt01ch37pyo01.md) 对象的类型。可能的值为 DEFORMABLE_BODY 和 ANALYTIC_RIGID_SURFACE。

**可选参数**

无。

**返回值**

OdbPart 对象。

**异常**

无。

### 34.19.2 addElements(...)

此方法使用单元标签和节点连接性向 OdbPart 对象添加单元。

**警告：**不按标签升序添加单元可能导致 Abaqus/Viewer 错误地绘制等值线。

**必要参数**

*labels*

整数序列，指定单元标签。

*connectivity*

整数序列的序列，指定节点连接性。

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

无。

### 34.19.3 addElements(...)

此方法使用单元标签序列和节点连接性向 OdbPart 对象添加单元。

**警告：**不按标签升序添加单元可能导致 Abaqus/Viewer 错误地绘制等值线。

**必要参数**

*elementData*

整数序列的序列，以形式 ((*label*, *c1*, *c2*, *c3*, *c4*), (*label*, *c1*, *c2*, *c3*, *c4*), ...) 指定单元标签和节点连接性。

*type*

一个字符串，指定单元类型。该值可以是用户定义的。

**可选参数**

*elementSetName*

一个字符串，为此元素集指定名称。默认值为 None。

*sectionCategory*

一个 [SectionCategory](pt01ch34pyo27.md) 对象，用于此元素集。

**返回值**

无

**异常**

无。

### 34.19.4 addNodes(...)

此方法使用节点标签和坐标向 OdbPart 对象添加节点。

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

无。

### 34.19.5 addNodes(...)

此方法使用节点标签和坐标序列向 OdbPart 对象添加节点。

**警告：**不按标签升序添加节点可能导致 Abaqus/Viewer 错误地绘制等值线。

**必要参数**

*nodeData*

元组序列，以形式 ((*label*, *x*, *y*, *z*), (*label*, *x*, *y*, *z*), ...) 指定节点标签和坐标。

**可选参数**

*nodeSetName*

一个字符串，为此节点集指定名称。默认值为 None。

**返回值**

无

**异常**

无。

### 34.19.6 assignBeamOrientation(...)

此方法为部件实例的区域分配梁截面方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*method*

一个 SymbolicConstant，指定分配方法。当前仅支持 N1_COSINES。

*vector*

三个浮点数序列，指定梁截面近似局部 ![](../graphics/ker_eqn00406.gif) 方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.19.7 assignMaterialOrientation(...)

此方法为部件实例的区域分配材料方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*localCSys*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

一个 Float，指定额外旋转的角度。默认值为 0.0。

*stackDirection*

一个 SymbolicConstant，指定材料的堆叠或厚度方向。可能的值为 STACK_1、STACK_2、STACK_3 和 STACK_ORIENTATION。默认值为 STACK_3。

**返回值**

无

**异常**

无。

### 34.19.8 assignRebarOrientation(...)

此方法为部件实例的区域分配钢筋参考方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*localCsys*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

一个 Float，指定额外旋转的角度。默认值为 0.0。

**返回值**

无

**异常**

无。

### 34.19.9 getElementFromLabel(...)

此方法用于从部件对象中检索具有特定标签的单元。

**必要参数**

*label*

一个整数，指定单元标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshElement](pt01ch34pyo17.md) 对象。

**异常**

如果不存在具有指定标签的单元：

```
OdbError: Invalid element label
```

### 34.19.10 getNodeFromLabel(...)

此方法用于从部件对象中检索具有特定标签的节点。

**必要参数**

*label*

一个整数，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 34.19.11 AnalyticRigidSurf2DPlanar(...)

此方法用于在部件对象上定义二维 [AnalyticSurface](pt01ch34pyo02.md) 对象。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

**返回值**

无

**异常**

如果 OdbPart 类型为 THREE_D：

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the part is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 34.19.12 AnalyticRigidSurfExtrude(...)

此方法用于在部件对象上定义三维圆柱形 [AnalyticSurface](pt01ch34pyo02.md)。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

**返回值**

无

**异常**

如果 OdbPart 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                            CYLINDER                            can be defined only if the part is of type                             THREE_D.                         
```

### 34.19.13 AnalyticRigidSurfRevolve(...)

此方法用于在部件对象上定义三维旋转 [AnalyticSurface](pt01ch34pyo02.md)。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

**返回值**

无

**异常**

如果 OdbPart 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the part is of type                             THREE_D.                         
```

### 34.19.14 RigidBody(...)

此方法在部件对象上定义一个 [OdbRigidBody](pt01ch34pyo21.md)。

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

### 34.19.15 成员

OdbPart 对象具有与 [Part](pt01ch34pyo19.md#ker-odbpart-part-pyc) 方法的参数名称和描述相同的成员。

此外，OdbPart 对象可以具有以下成员：

*nodes*

一个 [OdbMeshNodeArray](pt01ch34pyo18.md) 对象。

*elements*

一个 [OdbMeshElementArray](pt01ch34pyo17.md) 对象。

*nodeSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定节点集。

*elementSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定元素集。

*surfaces*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定曲面。

*sectionAssignments*

一个 [SectionAssignmentArray](pt01ch44pyo01.md) 对象。

*beamOrientations*

一个 [BeamOrientationArray](pt01ch34pyo04.md) 对象。

*materialOrientations*

一个 [MaterialOrientationArray](pt01ch44pyo04.md) 对象。

*rebarOrientations*

一个 [RebarOrientationArray](pt01ch34pyo25.md) 对象。

*rigidBodies*

一个 [OdbRigidBodyArray](pt01ch34pyo21.md) 对象。

*analyticSurface*

一个 [AnalyticSurface](pt01ch34pyo02.md) 对象，指定在实例上定义的解析曲面。
